# ubuntu 20.4

<pre>
NETWORK SETTING:
1. Modify  xxx.yaml file at /etc/netplan/xxx.yaml where yaml file is indent sensitive.
2. Find the name of ethernet.
3. This example is to setup the static address of ethernet.

</pre>
# Find the names of networking devices
<pre>
We must know device names including ethernet
The following ip command informs names of network devices (ethernet, wifi)
$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp0s25: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 04:20:9a:42:af:14 brd ff:ff:ff:ff:ff:ff
3: enx001de1550ccb: <NOARP> mtu 1400 qdisc noop state DOWN mode DEFAULT group default qlen 20
    link/ether 00:1d:e1:55:0c:cb brd ff:ff:ff:ff:ff:ff
4: wlp2s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 64:80:99:68:43:78 brd ff:ff:ff:ff:ff:ff

enp0s25 is the name of ethernet.
wlp2s0 is the WiFi name.
</pre>

# yaml file: ethernet static address
<pre>
network:
 version: 2
 renderer: networkd
 ethernets:
  enp0s25:
   dhcp4: no
   addresses:
   - 192.168.1.8/24
   gateway4: 192.168.1.1
   nameservers:
    addresses: [192.168.1.1]
</pre>    
To activate the yaml file on Ubuntu 20.4:

$ sudo netplan apply

# postfix mail

Read the following site:
https://github.com/ytakefuji/Mail-system

Modify main.cf file at /etc/postfix/main.cf

# apache2 web server using DynamicDNS

https://github.com/ytakefuji/http-to-https





