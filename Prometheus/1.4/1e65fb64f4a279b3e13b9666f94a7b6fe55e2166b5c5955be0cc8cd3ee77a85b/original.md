```
Prometheus.clear(family::Family)
```

Remove all collectors in the family. Effectively this resets the collectors since [`Prometheus.labels`](@ref) will recreate them when needed.

!!! note
    This method invalidates all cached collectors.

