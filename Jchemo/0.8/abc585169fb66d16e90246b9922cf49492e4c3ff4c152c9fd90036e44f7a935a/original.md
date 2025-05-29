```
plswold(; kwargs...)
plswold(X, Y; kwargs...)
plswold(X, Y, weights::Weight; kwargs...)
plswold!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

Partial Least Squares Regression (PLSR) with the Wold algorithm 

  * `X` : X-data (n, p).
  * `Y` : Y-data (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. latent variables (LVs) to compute.
  * `tol` : Tolerance for the Nipals algorithm.
  * `maxit` : Maximum number of iterations for the Nipals algorithm.
  * `scal` : Boolean. If `true`, each column of `X` and `Y`    is scaled by its uncorrected standard deviation.

Wold Nipals PLSR algorithm: Tenenhaus 1998 p.204.

See function `plskern` for examples.

## References

Tenenhaus, M., 1998. La régression PLS: thÃ©orie et pratique.  Editions Technip, Paris, France.

Wold, S., Ruhe, A., Wold, H., Dunn, III, W.J., 1984. The  Collinearity Problem in Linear Regression. The Partial Least  Squares (PLS). Approach to Generalized Inverses. SIAM Journal on  Scientific and Statistical Computing 5, 735–743.  https://doi.org/10.1137/0905052
