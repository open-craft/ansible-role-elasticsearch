# Ansible Role: Elasticsearch

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-elasticsearch.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-elasticsearch)

An Ansible Role that installs Elasticsearch on RedHat/CentOS or Debian/Ubuntu.

## Requirements

Requires at least Java 7 (Java 8+ preferred). See [`geerlingguy.java`](https://github.com/geerlingguy/ansible-role-java#example-playbook-install-openjdk-8) role instructions for installing OpenJDK 8.

## Role Variables
Available variables are listed below, along with default values (see `defaults/main.yml`):

    elasticsearch_network_host: localhost

Network host to listen for incoming connections on. By default we only listen on the localhost interface. Change this to the IP address to listen on a specific interface, or `0.0.0.0` to listen on all interfaces.

    elasticsearch_http_port: 9200

The port to listen for HTTP connections on.

    elasticsearch_script_inline: true
    elasticsearch_script_indexed: true

Whether to allow inline scripting against ElasticSearch. You should read the following link as there are possible security implications for enabling these options: [Enable Dynamic Scripting](https://www.elastic.co/guide/en/elasticsearch/reference/current/modules-scripting.html#enable-dynamic-scripting). Available options include: `true`, `false`, and `sandbox`.

    ENABLE_REVERSE_PROXY: false

Whether to configure a reverse proxy (nginx) in front of Elasticsearch. This is useful if you need to connect securely through the public internet.

    reverse_proxy_listen_port: 9201

Which port the reverse proxy should listen on to forward authenticated requests to Elasticsearch.

    reverse_proxy_auth_file: "/etc/nginx/.elasticsearch.passwd"

The location of the auth credentials file the role generates and uses.

    reverse_proxy_auth_username: admin
    reverse_proxy_auth_password: admin

The username and password needed to authenticate to Elasticsearch. **You should set this explicitly in production**.

## Dependencies

  - geerlingguy.java

## Example Playbook

    - hosts: search
      roles:
        - geerlingguy.java
        - geerlingguy.elasticsearch

## License

MIT / BSD

## Author Information

This role was created in 2014 by [Jeff Geerling](http://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
