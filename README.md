# A set of ansible tasks to install and configure multiple tomcat instances on a single node running on different ports
### Author: Shankar Balakrishna

##  ✨ Key Features  ✨

- Ability to configure ports independently on both instances
- Works with Zulu JDK and can be ported to work with Oracle JDK or Open JDK

### TODO: Add a JDK install step in the playbook if not found.

## Installation

Run install-tomcat.yml as is for the first time to create an Tomcat instance with the configuration in install-tomcat.yml
This should create a tomcat instance with the below config

```sh
    tomcat_major_version: 8
    tomcat_ver: 8.5.42
    ui_manager_user: manager
    ui_manager_pass: us3rp@ssw0rd
    ui_admin_username: admin
    ui_admin_pass: sh@nk@1@1ssw0rd
    JAVA_HOME: /usr/java/jdk-8
    tomcat_folder: tomcat1
    shut_down_port: 8005
    connector_port: 8080
    connector_redirect_port: 8443
    AJP_connector_port: 8009
    AJP_connector_redirect_port: 8345
```

Once this is done you can stop here and you will have a single instance of Tomcat running on port 8080.

#### Second Instance

In case you want an other instance, re-run the same playbook to create another tomcat instance by using the extra-vars option as below.


```sh
ansible-playbook tomcat-install.yml --extra-vars '{"tomcat_folder":"tomcat2","shut_down_port":"8006", "connector_port":"8090","connector_redirect_port":"8445","AJP_connector_port":"8010","AJP_connector_redirect_port":"8346"}'
```
