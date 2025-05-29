```
project(ℐ::Integral, domain::VectorSpace, codomain::VectorSpace, ::Type{T}=_coeftype(ℐ, domain, Float64))
```

Represent `ℐ` as a [`LinearOperator`](@ref) from `domain` to `codomain`.

See also: [`project!(::LinearOperator, ::Integral)`](@ref) and [`Integral`](@ref).
