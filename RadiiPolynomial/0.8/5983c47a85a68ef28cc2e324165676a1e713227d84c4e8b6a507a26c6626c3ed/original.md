```
opnorm(A::LinearOperator, p::Real=Inf)
```

Compute the operator norm of `A` induced by the `p`-norm. Only `p` equal to `1`, `2` or `Inf` is supported.

This is equivalent to:

  * `opnorm(A, Ell1(IdentityWeight()))` if `p == 1`
  * `opnorm(A, Ell2(IdentityWeight()))` if `p == 2`
  * `opnorm(A, EllInf(IdentityWeight()))` if `p == Inf`

See also: [`opnorm(::LinearOperator, ::BanachSpace)`](@ref), [`opnorm(::LinearOperator, ::BanachSpace, ::BanachSpace)`](@ref) and [`opnorm(::LinearOperator{<:VectorSpace,ParameterSpace}, ::BanachSpace)`](@ref).
