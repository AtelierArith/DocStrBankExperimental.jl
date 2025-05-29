```
Prometheus.Gauge(name, help; registry=DEFAULT_REGISTRY)
```

Construct a Gauge collector.

**Arguments**

  * `name :: String`: the name of the gauge metric.
  * `help :: String`: the documentation for the gauge metric.

**Keyword arguments**

  * `registry :: Prometheus.CollectorRegistry`: the registry in which to register the collector. If not specified the default registry is used. Pass `registry = nothing` to skip registration.

**Methods**

  * [`Prometheus.inc`](@ref inc(::Gauge, ::Real)): increment the value of the gauge.
  * [`Prometheus.dec`](@ref): decrement the value of the gauge.
  * [`Prometheus.set`](@ref): set the value of the gauge.
  * [`Prometheus.set_to_current_time`](@ref): set the value of the gauge to the current unixtime.
  * [`Prometheus.@time`](@ref): time a section and set the value of the the gauge to the elapsed time.
  * [`Prometheus.@inprogress`](@ref): Track number of inprogress operations; increment the gauge when entering the section, decrement it when leaving.
