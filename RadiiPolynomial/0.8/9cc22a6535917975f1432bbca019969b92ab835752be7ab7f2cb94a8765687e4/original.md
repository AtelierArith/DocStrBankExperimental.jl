```
opnorm(A::LinearOperator, X::BanachSpace)
```

Compute the operator norm of `A` where `X` is the Banach space corresponding to both `domain(A)` and `codomain(A)`.

See also: [`opnorm(::LinearOperator, ::Real=Inf)`](@ref), [`opnorm(::LinearOperator, ::BanachSpace, ::BanachSpace)`](@ref) and [`opnorm(::LinearOperator{<:VectorSpace,ParameterSpace}, ::BanachSpace)`](@ref).
