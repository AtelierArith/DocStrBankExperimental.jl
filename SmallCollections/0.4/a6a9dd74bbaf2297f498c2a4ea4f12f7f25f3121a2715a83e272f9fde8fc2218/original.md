```
addindex(v::V, x, i::Integer) where V <: AbstractCapacityVector -> V
```

Add `x` to the `i`-th component of `v` and return the new vector.

See also [`setindex`](@ref setindex(::AbstractCapacityVector, ::Any, i::Integer)).
