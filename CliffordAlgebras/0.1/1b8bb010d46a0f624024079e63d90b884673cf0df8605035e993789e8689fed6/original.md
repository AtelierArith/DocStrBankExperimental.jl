```
prune(::MultiVector ; rtol = 1e-8 )
```

Returns a new MultiVector with all basis vectors removed from the sparse basis whose coefficients fall below the relative magnitude threshold. This function is not type stable, because the return type depends on the sparse basis.
