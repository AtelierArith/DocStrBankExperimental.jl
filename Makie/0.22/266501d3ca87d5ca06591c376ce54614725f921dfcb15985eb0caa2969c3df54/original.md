```
Legend(fig_or_scene, axis::Union{Axis, Scene, LScene}, title = nothing; merge = false, unique = false, kwargs...)
```

Create a single-group legend with all plots from `axis` that have the attribute `label` set.

If `merge` is `true`, all plot objects with the same label will be layered on top of each other into one legend entry. If `unique` is `true`, all plot objects with the same plot type and label will be reduced to one occurrence.
