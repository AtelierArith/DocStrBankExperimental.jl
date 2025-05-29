```
truthtype(::Type{<:AbstractAlgebra{T}}) where {T<:Truth} = T
truthtype(a::AbstractAlgebra) = truthtype(typeof(a))
```

The Julia type for representing truth values of the algebra.

See also [`AbstractAlgebra`](@ref).
