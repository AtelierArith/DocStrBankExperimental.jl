```
empty(v::PackedVector{U,M}, S::Type) where {U,M,S} -> PackedVector{U,M,S}
```

Return an empty `PackedVector` with the same bit mask type and same bit size as `v`, but element type `S`.

See also [`empty(v::AbstractCapacityVector)`](@ref).
