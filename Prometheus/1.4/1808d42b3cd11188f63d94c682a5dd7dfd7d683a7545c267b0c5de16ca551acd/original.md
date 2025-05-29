```
expose(http::HTTP.Stream, reg::CollectorRegistry = DEFAULT_REGISTRY; kwargs...)
```

Export all metrics in `reg` by writing them to the HTTP stream `http`.

The caller is responsible for checking e.g. the HTTP method and URI target. For HEAD requests this method do not write a body, however.
