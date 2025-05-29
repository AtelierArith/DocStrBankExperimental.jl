```
opnorm(A::LinearOperator, X::BanachSpace, Y::BanachSpace)
```

Compute the operator norm of `A` where `X` is the Banach space corresponding to `domain(A)` and `Y` the Banach space corresponding to `codomain(A)`.

See also: [`opnorm(::LinearOperator, ::Real=Inf)`](@ref), [`opnorm(::LinearOperator, ::BanachSpace)`](@ref) and [`opnorm(::LinearOperator{<:VectorSpace,ParameterSpace}, ::BanachSpace)`](@ref).
