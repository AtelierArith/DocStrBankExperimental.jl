```
deartstest(X, Y)
```

Compute the DEA Returns to Scale (RTS) test using the bootstrap radial model for inputs X and outputs Y.

# Optional Arguments

  * `nreps=200`: number of bootstrap replications.
  * `rng=default_rng()`: random number generator.
  * `orient=:Input`: chooses the radially oriented input mode. For the radially oriented output model choose `:Output`.
