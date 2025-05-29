```
project(𝒟::Derivative, domain::VectorSpace, codomain::VectorSpace, ::Type{T}=_coeftype(𝒟, domain, Float64))
```

Represent `𝒟` as a [`LinearOperator`](@ref) from `domain` to `codomain`.

See also: [`project!(::LinearOperator, ::Derivative)`](@ref) and [`Derivative`](@ref).
