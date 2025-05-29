```
Prometheus.labels(family::Family{C}, label_values) where C
```

Get or create the collector of type `C` from the family corresponding to the labels given by `label_values`. If no collector exist for the input labels a new one is created by invoking the `C` constructor as `C(name, help, args...; kwargs..., registry=nothing)`, where `name`, `help`, `args...`, and `kwargs...` are the arguments from the family constructor, see [`Family`](@ref).

Similarly to when creating the [`Family`](@ref), `label_values` can be given as either of the following:

  * a tuple, e.g. `("/api", 200)`
  * a named tuple with names matching the label names, e.g.`(target="/api", status_code=200)`
  * a struct instance with field names matching the label names , e.g. `RequestLabels("/api", 200)`

All non-string values (e.g. `200` in the examples above) are stringified using `string`.

!!! tip
    `Base.getindex` is overloaded to have the meaning of `Prometheus.labels` for the family collector: `family[label_values]` is equivalent to `Prometheus.labels(family, label_values)`.


!!! note
    This method does an acquire/release of a lock, and a dictionary lookup, to find the collector matching the label names. For typical applications this overhead does not matter (below 100ns for some basic benchmarks) but it is safe to cache the returned collector if required.

