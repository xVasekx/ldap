Vagrant.configure("2") do |config|
    # Указываем ОС, версию, количество ядер и ОЗУ
#    config.vm.box = "generic/centos8"
 
    config.vm.provider :virtualbox do |v|
      v.memory = 2048
      v.cpus = 1
    end
  
    # Указываем имена хостов и их IP-адреса
    boxes = [
      { :name => "ipa.test.lan",
        :box_name => "generic/centos8",
        :ip => "192.168.57.10",
      },
      { :name => "client1.test.lan",
        :box_name => "generic/centos8",
        :ip => "192.168.57.11",
      },
      { :name => "client2.test.lan",
        :box_name => "ubuntu/xenial64",
        :ip => "192.168.57.12",
      }
    ]
    # Цикл запуска виртуальных машин
    boxes.each do |opts|
      config.vm.define opts[:name] do |config|
	config.vm.box = opts[:box_name]
        config.vm.hostname = opts[:name]
        config.vm.network "private_network", ip: opts[:ip]
      end
    end
  end
