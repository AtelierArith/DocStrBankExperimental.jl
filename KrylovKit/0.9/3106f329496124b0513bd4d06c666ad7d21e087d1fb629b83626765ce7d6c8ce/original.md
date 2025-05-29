```
initialize!(iter::KrylovIterator, fact::KrylovFactorization)
```

Initialize a length 1 Krylov factorization corresponding to `iter` in the already existing factorization `fact`, thereby destroying all the information it currently holds.
