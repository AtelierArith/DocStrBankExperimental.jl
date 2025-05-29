```
project(Δ::Laplacian, domain::VectorSpace, codomain::VectorSpace, ::Type{T}=_coeftype(Δ, domain, Float64))
```

Represent `Δ` as a [`LinearOperator`](@ref) from `domain` to `codomain`.

See also: [`project!(::LinearOperator, ::Laplacian)`](@ref) and [`Laplacian`](@ref).
