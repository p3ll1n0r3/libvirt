# libvirt

$ dnf install qemu-kvm libvirt virt-install virt-viewer

$ for drv in qemu network nodedev nwfilter secret storage interface; do systemctl start virt${drv}d{,-ro,-admin}.socket; done

$ virt-host-validate

$ nmcli connection add type vlan con-name enp5s0.100 dev enp5s0 id 100 ipv4.method disabled
$ nmcli connection add type bridge con-name br-vlan100 ifname br-vlan100 ipv4.method manual ipv4.addresses 192.168.100.1/24
$ nmcli connection add type bridge-slave ifname enp5s0.100 master br-vlan100

$ nmcli connection add type vlan con-name enp5s0.200 dev enp5s0 id 200 ipv4.method disabled
$ nmcli connection add type bridge con-name br-vlan200 ifname br-vlan200 ipv4.method manual ipv4.addresses 192.168.200.1/24
$ nmcli connection add type bridge-slave ifname enp5s0.200 master br-vlan100
