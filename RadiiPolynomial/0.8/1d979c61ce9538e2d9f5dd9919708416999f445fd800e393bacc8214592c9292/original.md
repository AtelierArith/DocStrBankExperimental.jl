```
project(𝒮::Shift, domain::VectorSpace, codomain::VectorSpace, ::Type{T}=_coeftype(𝒮, domain, Float64))
```

Represent `𝒮` as a [`LinearOperator`](@ref) from `domain` to `codomain`.

See also: [`project!(::LinearOperator, ::Shift)`](@ref) and [`Shift`](@ref).
