# Graphite Stack using Docker Playbook

Ansibile playbook to setup:
* [StatsD](https://github.com/etsy/statsd): listens for statistic and sends aggregates to backend service
* [CollectD](http://collectd.org): gathers metrics from various sources, e.g. the operating system, applications, logfiles and external devices, and stores this information or makes it available over the network
* [Graphite](https://graphiteapp.org/): montoring tools to store, retrieve, share, and visualize time-series data
* [Grafana](https://github.com/grafana/grafana): open source, feature rich metrics dashboard and graph editor for Graphite, Elasticsearch, OpenTSDB, Prometheus and InfluxDB

Requirements below will also be installed:
* Docker, on which containers will run
* Pip, package manager for python
* Certbot, bot to issue TLS certificate using ACME protocol
* nginx, web server

CollectD, certbot, docker, and nginx will be installed directly on host while others will be installed on top of Docker.

## Usage
Change `group_vars/all.yml` as you wish. `letsencrypt_email.yml` should contain
variable named `letsencrypt_email`. Please encrypt it using Ansible Vault.

```
ansible-galaxy install -r requirements.yml
ansible-playbook -i production site.yml --ask-vault-pass
```

## Author
Ricky Kurniawan

## Known Issue
* In certain Docker version, docker volume creation will fail if there is no docker volume yet in host.
