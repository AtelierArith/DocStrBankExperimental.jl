```
Prometheus.GCCollector(; registry=DEFAULT_REGISTRY)
```

Create a collector that exports metrics about allocations and garbage collection.

**Keyword arguments**

  * `registry :: Prometheus.CollectorRegistry`: the registry in which to register the collector. The default registry is used by default. Pass `registry = nothing` to skip registration.

!!! note
    A `GCCollector` is registered automatically with the default registry. If necessary it can be removed by calling

    ```julia
    Prometheus.unregister(Prometheus.DEFAULT_REGISTRY, Prometheus.GC_COLLECTOR)
    ```

