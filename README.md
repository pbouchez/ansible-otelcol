[![Actions Status - Master](https://github.com/juju4/ansible-otelcol/workflows/AnsibleCI/badge.svg)](https://github.com/juju4/ansible-otelcol/actions?query=branch%3Amain)
[![Actions Status - Devel](https://github.com/juju4/ansible-otelcol/workflows/AnsibleCI/badge.svg?branch=devel)](https://github.com/juju4/ansible-otelcol/actions?query=branch%3Adevel)

# OpenTelemetry Collector ansible role

Setup OpenTelemetry collector
* https://github.com/open-telemetry/opentelemetry-collector-contrib
* https://github.com/open-telemetry/opentelemetry-collector-releases/
* https://opentelemetry.io/docs/

## Requirements & Dependencies

### Ansible
It was tested on the following versions:
 * 2.10-17

### Operating systems

Tested on Ubuntu 24.04, 22.04, Centos/Rockylinux 9-10.

## Example Playbook

Just include this role in your list.
For example

```
- host: myhost
  roles:
    - juju4.otelcol
```

you probably want to review variables

## Variables

```
otelcol_version: 0.122.0
otelcol_hash: 'sha256:22a053fc960ca5e1b936a3e8b3060322ff0bcf04ae14ec46d77f40c8d495a322'
otelcol_config_template: otel-config.yaml
otelcol_user: _otel

otelcol_filelog_include: [ /var/log/**log ]
otelcol_debug_enable: false
otelcol_sampling_enable: false
# additional configuration (yaml input)
otelcol_journald_extras:
otelcol_config_receivers:
otelcol_config_processors:
otelcol_config_exporters:
otelcol_config_service_pipelines:
otelcol_config_connectors:

# To openobserve server?
# otelcol_server_url: https://SERVER/api/default/
otelcol_auth_key_retrieve: true
# otelcol_auth_key:
otelcol_get_certificate: false
# openobserve_root_user_email:
# openobserve_root_user_pass:
# otelcol_server_ansible_host:
# otelcol_server_crt_filepath: /etc/ssl/certs/OOSERVER.crt

install_archives: /var/_install
```

## Continuous integration

```
$ pip install molecule docker
$ molecule test
$ MOLECULE_DISTRO=ubuntu:24.04 molecule test --destroy=never
```


## Troubleshooting & Known issues

TBD

## License

BSD 2-clause
