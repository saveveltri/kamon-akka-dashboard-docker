# Prometheus and Grafana Docker-compose Stack for Kamon 2.0 for Akka 

This stack contains a prometheus container preconfigured with a kamon 2.0 target and a grafana container provisioned with a prometheus datasource and a comprehensive dashboard that visualize all the metrics gathered by kamon.

All credits for the grafana dashboards goes to 

https://grafana.com/grafana/dashboards/10776

# Pre-requisite

An akka application instrumented with kamon configured to report to prometheus must be running somewhere.

To add the prometheus reporter in kamon it's enough to add the following lines.

```
libraryDependencies += "io.kamon" %% "kamon-prometheus" % "2.0.0"
```

```
kamon {
  prometheus {
    embedded-server {
      hostname = 0.0.0.0
      port = 9095
    }
  }
}
```

# Configuration

[Here](prometheus/prometheus.yml#L29) it is possible to configure prometheus targets. In this example besides the default one, there is the `'host.docker.internal:9095'` wich relies on a kamon instrumented application configured as above running in the docker host machine.

