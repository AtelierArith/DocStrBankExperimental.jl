```
mlrchol()
mlrchol(X, Y)
mlrchol(X, Y, weights::Weight)
mlrchol!mlrchol!(X::Matrix, Y::Matrix, weights::Weight)
```

Compute a mutiple linear regression model (MLR) using the Normal equations      and a Choleski factorization.

  * `X` : X-data, with nb. columns >= 2 (required by function cholesky).
  * `Y` : Y-data (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Compute only a model with intercept.

Faster but can be less accurate (based on squared element X'X).

See function `mlr` for examples.
