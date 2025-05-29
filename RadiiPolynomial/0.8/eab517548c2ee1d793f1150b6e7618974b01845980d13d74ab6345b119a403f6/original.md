```
project(ℰ::Evaluation, domain::VectorSpace, codomain::VectorSpace, ::Type{T}=_coeftype(ℰ, domain, Float64))
```

Represent `ℰ` as a [`LinearOperator`](@ref) from `domain` to `codomain`.

See also: [`project!(::LinearOperator, ::Evaluation)`](@ref) and [`Evaluation`](@ref).
