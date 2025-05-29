```
plssimp(; kwargs...)
plssimp(X, Y; kwargs...)
plssimp(X, Y, weights::Weight; kwargs...)
plssimp!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

Partial Least Squares Regression (PLSR) with the SIMPLS algorithm (de Jong 1993).

  * `X` : X-data (n, p).
  * `Y` : Y-data (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. latent variables (LVs) to compute.
  * `scal` : Boolean. If `true`, each column of `X` and `Y`    is scaled by its uncorrected standard deviation.

**Note:** In this function, scores T (LVs) are not normed,  conversely to the original algorithm of de Jong (2013).

See function `plskern` for examples.

## References

de Jong, S., 1993. SIMPLS: An alternative approach to  partial least squares regression. Chemometrics and Intelligent  Laboratory Systems 18, 251–263.  https://doi.org/10.1016/0169-7439(93)85002-X
