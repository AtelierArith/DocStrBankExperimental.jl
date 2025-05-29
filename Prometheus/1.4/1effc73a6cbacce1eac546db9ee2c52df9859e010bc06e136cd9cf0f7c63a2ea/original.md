```
Prometheus.expose(file::String, reg::CollectorRegistry = DEFAULT_REGISTRY)
```

Export all metrics in `reg` by writing them to the file `file`.
