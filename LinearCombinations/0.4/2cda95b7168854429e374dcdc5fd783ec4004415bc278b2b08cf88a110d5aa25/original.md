```
termtype(::Type{L}) where L <: AbstractLinear{T,R} = T
termtype(a::L) where L <: AbstractLinear{T,R} = T
```

Return the type of the terms (basis elements) in a linear combination.

See also [`coefftype`](@ref).
