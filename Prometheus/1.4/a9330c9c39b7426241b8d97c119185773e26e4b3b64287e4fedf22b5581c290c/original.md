```
Prometheus.Summary(name, help; registry=DEFAULT_REGISTRY)
```

Construct a Summary collector.

**Arguments**

  * `name :: String`: the name of the summary metric.
  * `help :: String`: the documentation for the summary metric.

**Keyword arguments**

  * `registry :: Prometheus.CollectorRegistry`: the registry in which to register the collector. If not specified the default registry is used. Pass `registry = nothing` to skip registration.

**Methods**

  * [`Prometheus.observe`](@ref observe(::Summary, ::Real)): add an observation to the summary.
  * [`Prometheus.@time`](@ref): time a section and add the elapsed time as an observation.
