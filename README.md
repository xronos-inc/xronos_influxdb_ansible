# Provision InfluxDB for Xronos Applications

Provision a host with InfluxDB v2 configured for Xronos applications.

This role performs the following steps:

- Deploys custom configuration and security tokens to the remote host
- Runs InfluxDB in a docker container

## Requirements

Provisioning host:

- Ansible 2.15

Remote host:

- Ubuntu 22.04 or later
- docker

## Example playbook

```yaml
- hosts: influxdb
  gather_facts: true
  roles:
    - name: xronos_influxdb_ansible
      role: xronos_influxdb_ansible
      vars:
        # set your influx admin password here
        influxdb_admin_password: "" 
        # set your influx admin token here
        influxdb_admin_token:    ""
```

After running, the following services should be running:

- InfluxDB: `http://influxdb:8086`

## Variables

- `deployment` (= `xronos` ): The name of this deployment. Used to prefix filesystem and docker resources so that more than once instance of this service may coexist on the same host.
- `influxdb_path` (= `/opt/{{ deployment }}/influxdb` ): The path to store InfluxDB configuration.
- `influxdb_admin_password`: The password for the admin user when using the web interface.
- `influxdb_admin_token`: API token for the admin user.
