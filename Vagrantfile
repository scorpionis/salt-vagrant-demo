# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define :master do |master_config|
    master_config.vm.box = "ubuntu/trusty64"
    master_config.vm.host_name = 'saltmaster.local'
    master_config.vm.network "private_network", ip: "192.168.50.10"
    master_config.vm.synced_folder "saltstack/salt/", "/srv/salt"

    master_config.vm.provision :salt do |salt|
      salt.master_config = "saltstack/etc/master"
      #salt.install_type = "git"
      #salt.install_args = 'v2015.5.0'
      salt.install_master = true
      salt.no_minion = true
      salt.verbose = true
    end
  end

  config.vm.define :minion1 do |minion_config|
    minion_config.vm.box = "ubuntu/trusty64"
    minion_config.vm.host_name = 'saltminion1.local'
    minion_config.vm.network "private_network", ip: "192.168.50.11"

    minion_config.vm.provision :salt do |salt|
      salt.minion_config = "saltstack/etc/minion1"
      #salt.install_type = "git"
      #salt.install_args = 'v2015.5.0'
      salt.verbose = true
    end
  end

  config.vm.define :minion2 do |minion_config|
    minion_config.vm.box = "ubuntu/trusty64"
    # The following line can be uncommented to use Centos
    # instead of Ubuntu.
    # Comment out the above line as well
    #minion_config.vm.box = "chef/centos-6.5"
    minion_config.vm.host_name = 'saltminion2.local'
    minion_config.vm.network "private_network", ip: "192.168.50.12"

    minion_config.vm.provision :salt do |salt|
      salt.minion_config = "saltstack/etc/minion2"
      #salt.install_type = "git"
      #salt.install_args = 'v2015.5.0'
      salt.verbose = true
    end
  end

end
