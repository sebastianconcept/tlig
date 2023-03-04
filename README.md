# tlig
Telegraf Loki InfluxDB Grafana

[![License](https://img.shields.io/badge/license-MIT-green)](./LICENSE.txt)
[![Release](https://img.shields.io/github/v/tag/sebastianconcept/tlig?label=release)](https://github.com/sebastianconcept/tlig/releases)

### Applicability
Monitoring setup and GUI for operation performance monitoring using Grafana.

### Features
1. Promtail collects logs for Loki.
2. Loki provides datasource and querying features to Grafana.
3. Telegraf collects periodic performance metrics that saves in InfluxDB.
4. InfluxDB provides datasource and querying features to Grafana.
5. Grafana provides datasource consumption and a nice GUI for you.

### Start
```
docker-compose up -d --force-recreate
```

### Stop
```
docker-compose down
```
### First time setup
1. Open Grafana GUI http://localhost:3008 and, since it's the first time, login using `admin` `admin` and later change to proper credentials.

2. Go to `Add your first data source` and add Loki from the list.
    1. URL:  `http://loki:3100`.
    2. `Save & test`.
3. Go again to `Add your first data source` and add InfluxDB from the list.
    1. Query language: `Flux`.
    2. URL: `http://influxdb:8086`.
    3. Basic auth off.
    4. Organization: use what you have set for `DOCKER_INFLUXDB_INIT_ORG` in your `.env`file.
    5. `Save & test`.

With that done, you should be able to create Dashboards and panels that consume InfluxDB and Loki datasources.