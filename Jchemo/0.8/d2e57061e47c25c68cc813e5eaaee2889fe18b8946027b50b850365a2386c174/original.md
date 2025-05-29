```
plsnipals(; kwargs...)
plsnipals(X, Y; kwargs...)
plsnipals(X, Y, weights::Weight; kwargs...)
plsnipals!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

Partial Least Squares Regression (PLSR) with the Nipals algorithm.

  * `X` : X-data (n, p).
  * `Y` : Y-data (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. latent variables (LVs) to compute.
  * `scal` : Boolean. If `true`, each column of `X` and `Y`    is scaled by its uncorrected standard deviation.

In this function, for PLS2 (multivariate Y), the Nipals  iterations are replaced by a direct computation of the  PLS weights (w) by SVD decomposition of matrix X'Y  (Hoskuldsson 1988 p.213).

See function `plskern` for examples.

## References

Hoskuldsson, A., 1988. PLS regression methods. Journal of  Chemometrics 2, 211-228.https://doi.org/10.1002/cem.1180020306

Tenenhaus, M., 1998. La régression PLS: thÃ©orie et pratique.  Editions Technip, Paris, France.

Wold, S., Sjostrom, M., Eriksson, l., 2001. PLS-regression:  a basic tool for chemometrics. Chem. Int. Lab. Syst., 58, 109-130.
