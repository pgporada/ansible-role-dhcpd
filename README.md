pgporada.dhcpd
=========

Installs and configures dhcpd.


Requirements
------------

None


Role Variables
--------------

    dhcpd_domain: "house.intra"
    dhcpd_dnsservers:
      - 8.8.8.8
      - 8.8.4.4
    dhcpd_ntpservers:
      - 172.16.1.1

    dhcpd_default_lease_time: 86400
    dhcpd_max_lease_time: 86400
    dhcpd_authoritative: true
    dhcpd_log_facility: local0

    dhcpd_subnet_network: 172.16.1.0
    dhcpd_subnet_netmask: 255.255.255.0
    dhcpd_subnet_range_start: 172.16.1.100
    dhcpd_subnet_range_end: 172.16.1.200
    dhcpd_subnet_broadcast_addr: 172.16.1.255
    dhcpd_subnet_routers: 172.16.1.1


Dependencies
------------


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

GPLv3

References
----------
[http://prefetch.net/articles/iscdhcpd.html]()

[https://help.ubuntu.com/community/isc-dhcp-server]()

[https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Deployment_Guide/sect-Configuring_a_Multihomed_DHCP_Server.html]()

Troubleshooting
---------------

If there is only one subnet declaration, and no network interfaces are in the range of that subnet, the DHCP daemon fails to start, and an error such as the following is logged to /var/log/messages:

        dhcpd: No subnet declaration for eth0 (0.0.0.0).
        dhcpd: ** Ignoring requests on eth0.  If this is not what
        dhcpd:    you want, please write a subnet declaration
        dhcpd:    in your dhcpd.conf file for the network segment
        dhcpd:    to which interface eth1 is attached. **
        dhcpd:
        dhcpd:
        dhcpd: Not configured to listen on any interfaces!

Author Information
------------------
Phil Porada - philporada@gmail.com
