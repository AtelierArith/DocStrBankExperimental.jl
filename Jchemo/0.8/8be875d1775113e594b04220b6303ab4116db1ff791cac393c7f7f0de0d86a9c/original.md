```
matW(X, y, weights::Weight)
```

Within-class covariance matrices.

  * `X` : X-data (n, p).
  * `y` : A vector (n) defing the class membership.
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Compute the (non-corrected) within-class and pooled covariance  matrices  (outputs `Wi` and `W`, respectively) of `X`. 

If class i contains only one observation, Wi is computed by:

  * `covm(`X`,`weights`)`.

For examples, see function `matB`. 
