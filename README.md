Ansible-zookeeper - Ansible Playbook for zookeeper
=============
The ansible-zookeeper role supports the installation and configuration of a mesos cluster with options for master, slave or a master-slave setup. It is restricted to ubuntu environment.

Installation
-----------

Dependencies
------------
1. Java

Requirements
------------
Ansible version at least 2.0

Vault file creation process
------------
Move to the below folder and `remove the existing main.yml file`
>$cd Ansible-zookeeper/vars/

Now run the below mentioned command and create a password for the vault file

>$ansible-vault create main.yml 

Enter the below values in the vault file
```
---
ansible_connection: ssh
ansible_ssh_user: XXXX #user name of the host machine which should have sudo permission
ansible_ssh_pass: YYYY #Password for the username
ansible_sudo_pass: YYYY #Password for the username --> this will be used for sudo permissions
```
How to add the details in inventory
------------
```
[zookeeper]
hostname id=1 #please add the hostnames in the shown format
hostname id=2
hostname id=3

```
Example:
```
[zookeeper]
ec2-xx-xxx-xx-xxx.us-west-2.compute.amazonaws.com id=1
ec2-xx-xxx-xx-xxx.us-west-2.compute.amazonaws.com id=2
ec2-xx-xxx-xx-xxx.us-west-2.compute.amazonaws.com id=3
```

How to run 
------------
```ansible-playbook -i inventory -K all.yml --ask-vault ```

Author Information
------------------
[vakees](https://github.com/vakees1424)
