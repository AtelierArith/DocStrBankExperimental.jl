```
mlrvec(; kwargs...)
mlrvec(X, Y; kwargs...)
mlrvec(X, Y, weights::Weight; kwargs...)
mlrvec!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

Compute a simple (univariate x) linear regression model.

  * `x` : Univariate X-data (n).
  * `Y` : Y-data (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `noint` : Boolean. Define if the model is computed    with an intercept or not.

See function `mlr` for examples.
