Jira standalone
===============

CentOS 6 based Jira server.

## requirements

* the centos base image (CentOS 6.8 x64 from https://github.com/box-cutter/centos-vm)
* Ansible 2.x on your host machine
* Virtualbox
* Vagrant 1.8.x or better (for linked_clones)
* a Vagrant plugin (see below)

## Vagrant setup

an inventory for Vagrant is in *vagrant/hosts*, the hostname
in there must match your Vagrantfile.

We use  the [hostmanager plugin](https://github.com/smdahlen/vagrant-hostmanager)
for name resolution, so you'll need to run:

    vagrant plugin install vagrant-hostmanager

Then

    vagrant up

_NB: this will also (try to) edit your local /etc/hosts_

## setting things up

Run the play with:

    ansible-playbook -i vagrant/ site.yml

this will install Jira and a local mysql DB for it to use.

Jira doesn't make it easy to automate itself; so although we create
a DB and user you have to connect Jira to it yourself.

At the end of the play, ansible will output a message with what
you need to manually enter into the Jira UI.

You can also upload/create a license key, etc.

### BUGS

Oh, I expect so. Log an issue / PR if you notice any.
