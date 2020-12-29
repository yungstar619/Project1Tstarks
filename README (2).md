## Automated ELK Stack Deployment
The files in this repository were used to configure the network depicted below.

https://drive.google.com/file/d/1f1uOTH7yrEvcQPROmgnmD39q2ZDLABnT/view?usp=sharing


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - install-elk.yml is the file i used to deploy elk stack

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly Efficient, in addition restricting traffic to the network.
- What aspect of security do load balancers protect?
  Load balancers protect the network from DDOS(distributed denial of service) attacks.  
- What is the advantage of a jump box?
  The main advantage of a jumpbox is that it can be used as a single Gateway into a secure network or enviorment via ssh.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs
- What does Filebeat watch for?
  Log Files
- What does Metricbeat record?
  Metric Beat monitors the metrics from the operating systems running on the server. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name    | Function     | IP Address | Operating System |
|---------|--------------|------------|------------------|
| Jumpbox | Gateway      | 10.0.0.4   | Linux            |
| WEB 1   | VM DvWA (Con)| 10.0.0.5   | Linux            |
| WEB 2   | VM DVWA (Con)| 10.0.0.7   | Linux            |
| ELK     | VM (Monitor) | 10.2.0.3   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the loadbalncer can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- whitelisted IP addresses 40.75.51.246 

Machines within the network can only be accessed by ssh.
- Which machine did you allow to access your ELK VM?  
  Jumbox  
- What was its IP address?
  10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |     No              | 69.143,57.144        |
| Web 1 & 2|     No              | 10.0.0.4             |
| Elk      |     no              | 10.0.0.4 10.0.0.5    |
                                   10.0.0.7

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because automation saves time and limits the risk of human error.  


The playbook implements the following tasks:
- Installs the docker apt module
  Installs pip3 apt module
  Installs docker python module 
  Use sysctl module for more memory Download 
  launch docker container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- List the IP addresses of the machines you are monitoring_
  10.0.0.5
  10.0.07

We have installed the following Beats on these machines:
- Specify which Beats you successfully installed_
  Filebeat
  Metricbeat
  These Beats allow us to collect the following information from each machine:
- Filebeat collects log events on files that was specified by the admin and forwards them to Elastaticsearch, Logstash and Kibana (ELK) for manageable indexing 
  Metricbeats collects metrics from the operating system and services running on the specified server

### Using the Playbooke
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the YAML file to '/etc/ansible' directory.
- Update the  '/etc/ansible/hosts' file to include 'hosts' group, private IP address, the following line 'ansible_python_interpreter=/usr/bin/python3'
- Run the playbook, and navigate to 'curl localhost/setup.php to check that the installation worked as expected.


- Which file is the playbook?
  Filebeat-playbook.yml
  Metricbeat-playbook.yml
  Ansible-config.yml
- Where do you copy it?
  etc/ansible 
- Which file do you update to make Ansible run the playbook on a specific machine? 
  by updating 'etc/ansible/hosts' with ips of the machines desired to be configured you may be able to run playbooks on thos specific machines. 
  How do I specify which machine to install the ELK server on versus which to install Filebeat on?
  by understanding that the Elk server is the ids that uses filebeat to monitor other client severs you would recognigze the importance of filebeat being installed on the client server and elk being installed on 
  a seperate server as to be a destination to forward logs to.  
- Which URL do you navigate to in order to check that the ELK server is running?
  http : // VM’s IP:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
