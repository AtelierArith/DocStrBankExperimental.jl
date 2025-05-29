```
mlrpinvn() 
mlrpinvn(X, Y)
mlrpinvn(X, Y, weights::Weight)
mlrpinvn!mlrchol!(X::Matrix, Y::Matrix, 
    weights::Weight)
```

Compute a mutiple linear regression model (MLR)      by using the Normal equations and a pseudo-inverse.

  * `X` : X-data (n, p).
  * `Y` : Y-data (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Safe and fast for p not too large.

Compute only a model with intercept.

See function `mlr` for examples.
