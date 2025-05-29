```
Prometheus.remove(family::Family, label_values)
```

Remove the collector corresponding to `label_values`. Effectively this resets the collector since [`Prometheus.labels`](@ref) will recreate the collector when called with the same label names.

Refer to [`Prometheus.labels`](@ref) for how to specify `label_values`.

!!! note
    This method invalidates cached collectors for the label names.

