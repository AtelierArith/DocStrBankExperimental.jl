```
setindex(v::V, x, i::Integer) where V <: AbstractCapacityVector -> V
```

Substitute `x` for the `i`-th component of `v` and return the new vector.

See also `Base.setindex`,  [`addindex`](@ref addindex(::AbstractCapacityVector, ::Any, i::Integer)).
