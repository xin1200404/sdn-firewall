## README for Final Project: Implementing a Simple Router ##

---------------------------------------------------

Xinyi Ping, 06/03/2026
email: xiping@ucsc.edu
CruzID: xiping
student ID: 2245279

---------------------------------------------------

## final_skel.py ##
This is mininet topology file. This file is to create switches, hosts, and links for the network

## finalcontroller_skel.py ##
This is controller file. This file is to implement logic and firewall rules

## project.pdf ##
This is final project report containing screenshots and explanations to all final project assingments

## README ##
This is this file. It describes the contents of each file in final project

---------------------------------------------------

## Switches ##
Core switch: s1
Floor 1 switches: s2, s3
Floor 2 switches: s4, s5
Data center switch: s6

## Hosts ##
Floor 1 hosts (Department A hosts): h101, h102, h103, h104
Floor 2 hosts (Department B hosts): h201, h202, h203, h204
Trusted host: h_trust
UNtrusted host: h_untrust
LLM server: h_server

## Filewall Rules ##
Block all IP traffic from the untrusted host to the server.
Block all ICMP traffic from the untrusted host to anywhere internally (Host 101-104, Host 201-204 and the LLM Server).
Allow traffic from the trusted host to Department A hosts. 
Block all ICMP and IP traffic from the trusted host to the server.
Block all ICMP traffic from the trusted host to Department B hosts.
Block all ICMP traffic between Department A and Department B hosts.
Allow all other valid traffic.
Flood only non-IP traffic.
Forward IP traffic using explicit switch ports.

---------------------------------------------------
## Usage ##
Run "sudo ~/pox/pox.py misc.finalcontroller_skel" to launch the controller
Run "sudo python ~/final_skel.py" to run the mininet file
Run "nodes", "net" to check the mininet topology
Run "h101 ifconfig", "h202 ifconfig", "h_trust ifconfig", "h_untrust ifconfig", "h_server ifconfig" to check the IP address
Run "h101 ping -c 3 h102", "h_trust ping -c 3 h102" to test the allowed coomunication
Run "h_untrust ping -c 2 h101", "h_untrust ping -c 2 h201", "h_untrust ping -c 2 h_server", "h_trust ping -c 2 h201", "h101 ping -c 3 h201" to test the blocked ICMP traffic
Run "h201 iperf -s &", "h_trust iperf -c 128.114.2.201" to test allowed TCP traffic
Run "h101 ping -c 1 h103", "dpctl dump-flows" to get the flow tables

All required tasks were completed and documented in project.pdf
