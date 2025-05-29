```
apply_factorization(A, factfun)
```

Apply a matrix factorization to the primal portion of a dual number. Avoids user from needing to add ForwardDiff as a dependency. `Afactorization = factfun(A)`
