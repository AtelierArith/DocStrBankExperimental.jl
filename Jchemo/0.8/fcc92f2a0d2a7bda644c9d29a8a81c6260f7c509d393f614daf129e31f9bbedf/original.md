```
mlrpinv()
mlrpinv(X, Y; kwargs...)
mlrpinv(X, Y, weights::Weight; kwargs...)
mlrpinv!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

Compute a mutiple linear regression model (MLR)  by using      a pseudo-inverse. 

  * `X` : X-data (n, p).
  * `Y` : Y-data (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `noint` : Boolean. Define if the model is computed    with an intercept or not.

Safe but can be slower.  

See function `mlr` for examples.
