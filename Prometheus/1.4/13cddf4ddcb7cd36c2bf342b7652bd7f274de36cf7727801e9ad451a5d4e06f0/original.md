```
Prometheus.ProcessCollector(pid; registry=DEFAULT_REGISTRY)
```

Create a process collector for the process id given by the `pid` function. The collector exposes metrics about the process' CPU time, start time, memory usage, file usage, and I/O operations.

**Arguments**

  * `pid :: Function`: a function returning a process id as a string or integer for which to collect metrics. By default the `"self"` pid is used, i.e. the current process.

**Keyword arguments**

  * `registry :: Prometheus.CollectorRegistry`: the registry in which to register the collector. The default registry is used by default. Pass `registry = nothing` to skip registration.

!!! note
    A `ProcessCollector` for the current process is registered automatically with the default registry. If necessary it can be removed by calling

    ```julia
    Prometheus.unregister(Prometheus.DEFAULT_REGISTRY, Prometheus.PROCESS_COLLECTOR)
    ```


!!! note
    The process collector is currently only available on Linux since it requires the `/proc` file system. On Windows and macOS this collector will not expose any metrics.

