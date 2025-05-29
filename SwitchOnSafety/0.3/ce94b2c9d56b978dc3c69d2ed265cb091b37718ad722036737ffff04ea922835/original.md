```
invariant_sets!(sets, modes_to_compute, system::AbstractHybridSystem,
                args...; kwargs...)
```

Similar to `invariant_sets(system, args...; kwargs...)` but stores the result in `sets` and only compute the modes in `modes_to_compute`. The other sets in `enabled` that are not in `modes_to_compute` are assumed to have the value given in `sets`.
