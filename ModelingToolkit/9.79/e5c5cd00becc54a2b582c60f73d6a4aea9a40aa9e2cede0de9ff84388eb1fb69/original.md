```
reorder_dimension_by_tunables!(dest::AbstractArray, sys::AbstractSystem, arr::AbstractArray, syms; dim = 1)
```

Assuming the order of values in dimension `dim` of `arr` correspond to the order of tunable parameters in the system, reorder them according to the order described in `syms`. `syms` must be a permutation of `tunable_parameters(sys)`. The result is written to `dest`. The `size` of `dest` and `arr` must be equal. Return `dest`.

See also: [`MTKParameters`](@ref), [`tunable_parameters`](@ref), [`reorder_dimension_by_tunables`](@ref).
