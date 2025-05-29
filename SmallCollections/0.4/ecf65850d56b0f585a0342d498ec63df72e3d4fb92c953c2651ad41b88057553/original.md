```
pop(s::AbstractSmallSet{N,T}, x) where {N,T} -> Tuple{SmallSet{N,T}, T}
```

Remove the element `x` from `s` and return the new set together with the stored element equal to `x`.

See also `Base.pop!`, [`delete`](@ref delete(::AbstractSmallSet, ::Any)).
