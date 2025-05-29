```
coefftype(::Type{L}) where L <: AbstractLinear{T,R} = R
coefftype(a::L) where L <: AbstractLinear{T,R} = R
```

Return the type of the coefficients in a linear combination.

See also [`termtype`](@ref).
