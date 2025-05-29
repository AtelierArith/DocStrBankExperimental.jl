```
normres(fact::KrylovFactorization)
```

Return the norm of the residual of a [`KrylovFactorization`](@ref). As this has typically already been computed, it is cheaper than (but otherwise equivalent to) `norm(residual(F))`.
