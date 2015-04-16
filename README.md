# Cisco OpenStack Private Cloud Application Demo

This set of tools is to demonstrate a continuous integration environment
on Cisco OpenStack Private Cloud (COPC) previously known as Metacloud. 

The idea is to show how we can quickly get code from development to 
production using automated testing.  This is to answer the question from 
continuous delivery of: "How long does it take for you to get one line of
code change into production"

## Components

* Provisioning
** Ansible - To get environment up. 
** Packer - To create images that can be used as Jenkins slaves. 

* Docker Containers used
** Docker Registry
** Ruby:2.2.1
** Jenkins
** sameersbn/gitlab
** Ubuntu 

* OpenStack Images Required
** CoreOS 
** Ubuntu 14.04 to run the sample application

## Prereqs

* You will need coreos bootstrap https://github.com/defunctzombie/ansible-coreos-bootstrap 

## Usage

You will need to define the following environment variables:

* OS_USERNAME="bilbo"
* OS_PASSWORD=supersecret
* OS_AUTH_URL=http://yourmetacloudidentityservice:5000/v2.0
* OS_TENANT_ID=123456789101112131415
* OS_TENANT_NAME='Ring Project'

This can be easily done by navigating to the Access & Security navigation bar in Metacloud, selecting API Access and then 'Download Openstack RC file'.  This will create a file you can append to your ~/.bash_profile.


In addition you'll need to define variables that are inside the main vars/ directory.  
These are security groups and ip pools. 

### Encryption

I use Ansible Vault to maintain passwords.  To see how this was created and secured, [See this writeup](http://benincosa.com/?p=3235)
