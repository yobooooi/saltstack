Vagrant.configure("2") do |config|
    
    #TODO: add ansible to install and to set the finger print of the salt minons 
	config.vm.define "saltmaster" do |saltmaster|
		saltmaster.vm.box = "ubuntu/focal64"
		saltmaster.vm.network "private_network", ip: "192.168.50.8"
        saltmaster.vm.network "public_network"
		saltmaster.vm.provider :virtualbox do |vb|
            vb.customize [
                "modifyvm", :id,
                "--cpuexecutioncap", "50",
                "--memory", "2048",
                "--audio", "none",
                "--uart1", "0x3F8", "4",
                "--uartmode1", "file", File::NULL
            ]
        end
        config.vm.hostname = "salt-master"
		saltmaster.vm.provision :shell do |shell|
            shell.inline = "sudo locale-gen UTF-8;
                            sudo apt-get update;"
		end
    end

    config.vm.define "saltminion1" do |saltminion1|
		saltminion1.vm.box = "ubuntu/focal64"
		saltminion1.vm.network "private_network", ip: "192.168.50.10"
        saltminion1.vm.network "public_network"
		saltminion1.vm.provider :virtualbox do |vb|
            vb.customize [
                "modifyvm", :id,
                "--cpuexecutioncap", "50",
                "--memory", "512",
                "--audio", "none",
                "--uart1", "0x3F8", "4",
                "--uartmode1", "file", File::NULL
            ]
        end
        config.vm.hostname = "salt-minion-1"
		saltminion1.vm.provision :shell do |shell|
            shell.inline = "sudo locale-gen UTF-8;
                            sudo apt-get update;"
		end
    end
end
