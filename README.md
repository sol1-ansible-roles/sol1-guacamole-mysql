Ansible Role: Guacamole
=========

This Ansible role will configure Apache's Guacamole on Debian 10
complete with MariaDB and LDAP auth plugins.

It is *strongly* advised that you run `mysql_secure_installation` after this is run. This role does *not* create a MariaDB root password.

This role is getting split out into different roles, for guacamole client (the tomcat application), guacamole server (guacd), and guacamole mysql.
Splitting the role will mean we can have seperate machines perform these functions, with firewall rules in between, to improve the security of each componenent.


Requirements
------------

Works with Ansible 2.4.

Requires `become` or running as the `root` user. You can use `--ask-become-pass` when running.

Role Variables
--------------
The following variables are set in `defaults/main`:

| Variable                 | Description                  |
|--------------------------|------------------------------|
|guacamole_version         | Guacamole version to install |
|guacamole_db_user         | Guacamole MariaDB username   |
|guacamole_db_password     | Guacamole MariaDB password   |
|guacamole_db_name         | Guacamole MariaDB database   |
|mysql_java_client_version | MySQL Java Client version    |
|guacamole_apt_install     | Apt packages to install      |

Example Playbook
----------------

```
- hosts: guacamole-host
  become: yes
  roles:
    - alexfeig.guacamole
```

 Information
------------------

This role was created by [Alex Feigenson](https://github.com/alexfeig) and updated by [Sol1](https://sol1.com.au)

To Do List
------------------

* Maybe add in an nginx proxy
* Make MariaDB an optional install
* Add travis integration (need to account for 16.04)
