```
dismantle_ci_oneiter!(g, heap, lneigs, l)
```

One step of [`dismantle_ci`](@ref) algorithm. To be called after [`dismantle_ci_init`](@ref) Returns the cleaned vertex if any (see [`clean_vertex!`](@ref)), -1 otherwise.
