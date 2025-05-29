```
plsrosa(; kwargs...)
plsrosa(X, Y; kwargs...)
plsrosa(X, Y, weights::Weight; kwargs...)
plsrosa!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

Partial Least Squares Regression (PLSR) with the  ROSA algorithm (Liland et al. 2016).

  * `X` : X-data (n, p).
  * `Y` : Y-data (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. latent variables (LVs) to compute.
  * `scal` : Boolean. If `true`, each column of `X` and `Y`    is scaled by its uncorrected standard deviation.

**Note:** The function has the following differences with  the original algorithm of Liland et al. (2016):

  * Scores T (LVs) are not normed.
  * Multivariate Y is allowed.

See function `plskern` for examples.

## References

Liland, K.H., Næs, T., Indahl, U.G., 2016. ROSA—a fast  extension of partial least squares regression for multiblock  data analysis. Journal of Chemometrics 30, 651–662.  https://doi.org/10.1002/cem.2824
