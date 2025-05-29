```
project(𝒮::Scale, domain::VectorSpace, codomain::VectorSpace, ::Type{T}=_coeftype(𝒮, domain, Float64))
```

Represent `𝒮` as a [`LinearOperator`](@ref) from `domain` to `codomain`.

See also: [`project!(::LinearOperator, ::Scale)`](@ref) and [`Scale`](@ref)
