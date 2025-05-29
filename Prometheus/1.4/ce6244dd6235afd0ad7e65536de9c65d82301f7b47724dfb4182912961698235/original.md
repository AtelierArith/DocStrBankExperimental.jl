```
Prometheus.Histogram(name, help; buckets=DEFAULT_BUCKETS, registry=DEFAULT_REGISTRY)
```

Construct a Histogram collector.

**Arguments**

  * `name :: String`: the name of the histogram metric.
  * `help :: String`: the documentation for the histogram metric.

**Keyword arguments**

  * `buckets :: Vector{Float64}`: the upper bounds for the histogram buckets. The buckets must be sorted. `Inf` will be added as a last bucket if not already included. The default buckets are `DEFAULT_BUCKETS = [0.005, 0.01, 0.025, 0.05, 0.075, 0.1, 0.25, 0.5, 0.75, 1.0, 2.5, 5.0, 7.5, 10.0, Inf]`.
  * `registry :: Prometheus.CollectorRegistry`: the registry in which to register the collector. If not specified the default registry is used. Pass `registry = nothing` to skip registration.

**Methods**

  * [`Prometheus.observe`](@ref): add an observation to the histogram.
  * [`Prometheus.@time`](@ref): time a section and add the elapsed time as an observation.
