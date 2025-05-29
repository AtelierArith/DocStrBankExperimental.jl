```
shrink!(fact::KrylovFactorization, k)
```

Shrink an existing Krylov factorization `fact` down to have length `k`. Does nothing if `length(fact)<=k`.
