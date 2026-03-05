Enterprise Network Architecture Simulation
Project Overview

This project demonstrates the design and implementation of a scalable and secure enterprise network architecture simulated using Cisco Packet Tracer.

The network is designed following a three-tier hierarchical model (Core – Distribution – Access) supporting multiple organizational departments including Guests, Employees, Management, HR, IT, Security, Voice systems, IoT devices, and centralized infrastructure services.

The main design objectives of this project were:

Network segmentation through VLANs and subnetting

High availability and redundancy

Dynamic and scalable routing

Centralized infrastructure services

Enterprise-grade security practices

The final topology integrates technologies such as OSPF, HSRP, STP, VLAN segmentation, ACLs, DHCP Snooping, Port Security, SSH management, NAT, DHCP, NTP, and Syslog to simulate a realistic enterprise network environment.

Network Architecture

The network follows the Cisco three-tier hierarchical design model, consisting of Core, Distribution, and Access layers.

Core Layer

The Core Layer provides high-speed Layer 3 connectivity and acts as the backbone of the network.

Two core switches are implemented to ensure redundancy and fault tolerance, allowing the network to remain operational in case of a device or link failure.

The core layer connects upstream to firewall devices responsible for NAT translation, enabling internal users to access external networks (Internet).

Distribution Layer

The Distribution Layer is implemented using Layer 3 switches and serves as the main policy enforcement and routing layer of the network.

Responsibilities of the distribution layer include:

Inter-VLAN routing via SVIs

Default gateway redundancy using HSRP

ACL enforcement between VLANs

Spanning Tree root bridge placement

Aggregation of multiple access switches

Three distribution switches are used to improve scalability and load balancing across the network.

Access Layer

The Access Layer consists of Layer 2 switches responsible for connecting end devices such as workstations, IP phones, and IoT devices.

These switches provide:

VLAN membership assignment

Port security protections

DHCP Snooping protection

Voice VLAN support

Secure uplinks to distribution switches

Security features such as PortFast and BPDU Guard are enabled on host ports to improve performance and prevent potential spanning-tree attacks or accidental loops.

VLAN Segmentation and IP Addressing

The network is segmented using multiple VLANs to isolate departments and services, improving both security and traffic management.

Subnetting was implemented to support approximately 64 hosts per VLAN, allowing room for organizational growth while maintaining manageable broadcast domains.

VLAN	Department
10	Guests
20	Employees
30	Management
40	HR
50	IT
60	Security
70	Voice
80	IoT
99	Network Infrastructure
100	Servers

VLAN segmentation helps enforce security boundaries between departments while allowing controlled access through routing policies.

Routing and High Availability
OSPF – Dynamic Routing

All Layer 3 devices participate in OSPF to provide dynamic routing across the network.

OSPF ensures:

Efficient route exchange

Automatic convergence during network changes

Scalability for future network expansion

Passive interfaces are used on host-facing links to reduce unnecessary routing traffic.

HSRP – Default Gateway Redundancy

HSRP is implemented on the distribution layer to provide redundant default gateways for VLANs.

Different distribution switches act as active gateways for different VLANs, distributing gateway responsibilities across devices to improve load balancing and network resilience.

This ensures that if one distribution switch fails, another device can automatically take over gateway responsibilities.

Spanning Tree Design

Rapid Spanning Tree Protocol (RSTP) is used to prevent switching loops while maintaining fast convergence.

The distribution layer switches are configured as the primary and secondary root bridges, following best practices where higher-capability switches control the spanning-tree topology.

Additional protections include:

PortFast on host ports to accelerate device connectivity

BPDU Guard to protect against accidental or malicious switch connections

Native VLAN changed to VLAN 999 as a security best practice

These measures help prevent broadcast storms and maintain network stability.

Network Security Implementation

Multiple security mechanisms were implemented to simulate a secure enterprise environment.

Access Control Lists (ACLs)

ACLs enforce network access policies between VLANs to ensure the least privilege principle, allowing each department to access only the resources required for its role.

Guest VLAN → Internet access only

Employees, HR, Security, Voice, IoT → Internet + server access

Management VLAN → Access to infrastructure devices, servers, and internet

IT VLAN → Full administrative access across the network

This design ensures departments can only access resources necessary for their operational role, reinforcing segmentation and security boundaries.

Secure Device Management

Network devices are secured using:

SSH version 2 for remote management

Telnet disabled

Access limited to authorized administrative VLANs

This ensures encrypted and controlled access to network infrastructure devices.

Layer 2 Security

Additional protections were implemented at the access layer.

DHCP Snooping

Prevents rogue DHCP servers from assigning unauthorized IP configurations.

Port Security

Limits the number of MAC addresses allowed on access ports, helping prevent unauthorized devices from connecting to the network.

Centralized Network Services

To simulate a realistic enterprise environment, multiple infrastructure services were centralized in the Server VLAN.

DHCP Server

Provides automatic IP address allocation for client devices across VLANs.

NTP Server

Ensures synchronized system time across network devices.

Syslog Server

Centralizes logging from network devices for monitoring and troubleshooting.

Internet Connectivity

Internet access is provided through firewall devices performing Network Address Translation (NAT).

NAT allows internal private networks to access external networks while maintaining internal address privacy.
