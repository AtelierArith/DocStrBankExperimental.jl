```
residual(fact::KrylovFactorization)
```

Return the residual of a [`KrylovFactorization`](@ref). The return type is some vector of the same type as used in the problem. See also [`normres(F)`](@ref) for its norm, which typically has been computed already.
