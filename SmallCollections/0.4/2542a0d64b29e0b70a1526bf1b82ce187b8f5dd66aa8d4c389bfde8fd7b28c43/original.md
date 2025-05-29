```
delete(s::AbstractSmallSet{N,T}, x) where {N,T} -> SmallSet{N,T}
```

Remove the element `x` from `s` (if it exists) and return the new set.

See also `Base.delete!`, [`pop`](@ref pop(::AbstractSmallSet, ::Any)).
