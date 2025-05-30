```
plan_map2salm(map, spin, ℓmax)
```

Precompute values to use in executing [`map2salm`](@ref) or [`map2salm!`](@ref).

The arguments to this function exactly mirror those of the first form of [`map2salm`](@ref), and all but the first argument in the first form of [`map2salm!`](@ref).  The `plan` returned by this function can be passed to the second forms of those functions to avoid some computation and allocation costs.

Note that the `plan` object is not thread safe; a separate `plan` should be created for each thread that will use one, or locks should be used to ensure that a single `plan` is not used at the same time on different threads.
