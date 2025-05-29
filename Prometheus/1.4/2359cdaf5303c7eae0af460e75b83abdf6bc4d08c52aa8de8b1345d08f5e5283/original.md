```
Prometheus.Counter(name, help; registry=DEFAULT_REGISTRY)
```

Construct a Counter collector.

**Arguments**

  * `name :: String`: the name of the counter metric.
  * `help :: String`: the documentation for the counter metric.

**Keyword arguments**

  * `registry :: Prometheus.CollectorRegistry`: the registry in which to register the collector. If not specified the default registry is used. Pass `registry = nothing` to skip registration.

**Methods**

  * [`Prometheus.inc`](@ref): increment the counter.
