VAGRANTFILE_API_VERSION ||= "2"

box = "box-cutter/ubuntu1604-desktop"
name = "vagrant-ansible-dev"
hostname = "desktop"
cpu = "2"
mem = "8048"
ipaddr = "192.168.0.90"
playbook = "ansible/playbook.yml"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
	config.vm.box_check_update = false

	config.vm.define name, primary: true do |app|
		app.vm.box = box
		app.vm.hostname = hostname
		app.vm.network :private_network, ip: ipaddr
		app.vm.provider :virtualbox do |vb|
			vb.name = name
			vb.cpus = cpu
			vb.memory = mem
			vb.gui = true
		end
		app.vm.provision :ansible_local do |ansible|
			ansible.playbook = playbook
		end
	end
end
