# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "debian/bookworm64"
  config.vm.define :master do |master|
    master.vm.network "private_network", ip: "192.168.57.101"
    master.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y bind9 dnsutils
    SHELL
    master.vm.provision "shell", name: "master-dns", inline: <<-SHELL
    cp -v /vagrant/named /etc/default/
    systemctl restart named
    SHELL
  end
end
