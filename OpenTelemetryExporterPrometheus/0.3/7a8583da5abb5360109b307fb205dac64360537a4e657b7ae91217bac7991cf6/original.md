```
PrometheusExporter(; kw...)
```

## Keyword arguments

  * `host`, the default value is read from the `OTEL_EXPORTER_PROMETHEUS_HOST` environment variable.
  * `port`, the default value is read from the `OTEL_EXPORTER_PROMETHEUS_PORT` environment variable.
  * `resource_to_telemetry_conversion=false`, if enabled, all the resource attributes will be converted to metric labels by default.
  * `path="/metrics"`, the default url path.

## Usage

```julia
r = MetricReader(PrometheusExporter())
```

Note that `PrometheusExporter` is a pull based exporter. There's no need to execute `r()` to update the metrics.
