```
empty(v::AbstractSmallVector{N}, S::Type) where {N,S} -> AbstractSmallVector{N,S}
```

Return an empty `AbstractSmallVector` with the same capacity as `v` and element type `U`. The resulting vector is mutable if and only if `v` is so.

See also [`empty(v::AbstractCapacityVector)`](@ref).
