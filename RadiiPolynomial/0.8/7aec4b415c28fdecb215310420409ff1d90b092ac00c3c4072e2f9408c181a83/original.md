```
opnorm(A::LinearOperator{<:VectorSpace,ParameterSpace}, X::BanachSpace)
```

Compute the operator norm of `A` where `X` is the Banach space corresponding to `domain(A)`.

See also: [`opnorm(::LinearOperator, ::Real=Inf)`](@ref), [`opnorm(::LinearOperator, ::BanachSpace, ::BanachSpace)`](@ref) and [`opnorm(::LinearOperator, ::BanachSpace)`](@ref).
