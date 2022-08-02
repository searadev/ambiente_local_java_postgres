# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  ## Escolha da Box
  config.vm.box = "ubuntu/focal64"
  ##config.vm.network :forwarded_port, guest: 8080, host: 5555, host_ip: "127.0.0.1" 
  config.vm.network "private_network", ip: "192.168.33.11"

  ## Configurações da VM
  config.vm.define 'seara' do |seara|

    seara.vm.hostname = "seara"
    seara.vm.provider "virtualbox" do |v|
      v.name = "seara"
      v.memory = 2048
      v.cpus = 2
    end

    seara.vm.provision :ansible_local do |ansible|
      ansible.install  = true
      ansible.install_mode = "default"
      ansible.playbook = "ansible/playbook.yml"
      ansible.inventory_path = "ansible/inventory"
      ansible.verbose  = true
      ansible.limit    = "all" 
    end
  end
end