```
kplskdeda(; kwargs...)
kplskdeda(X, y; kwargs...)
kplskdeda(X, y, weights::Weight; kwargs...)
```

KPLS-KDEDA.

  * `X` : X-data (n, p).
  * `y` : Univariate class membership (n).
  * `weights` : Weights (n) of the observations. Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. latent variables (LVs) to compute. Must be >= 1.
  * `kern` : Type of kernel used to compute the Gram matrices. Possible values are: `:krbf`, `:kpol`. See respective    functions `krbf` and `kpol` for their keyword arguments.
  * `prior` : Type of prior probabilities for class membership. Possible values are: `:prop` (proportionnal),    `:unif` (uniform), or a vector (of length equal to the number of classes) giving the prior weight for each class    (in case of vector, it must be sorted in the same order as `mlev(y)`).
  * Keyword arguments of function `dmkern` (bandwidth    definition) can also be specified here.
  * `scal` : Boolean. If `true`, each column of `X` and Ydummy is scaled by its uncorrected standard deviation   in the PLS computation.

Same as function `plskdeda` (PLS-KDEDA) except that a kernel PLSR (function `kplsr`), instead of a  PLSR (function `plskern`),  is run on the Y-dummy table. 

See function `kplslda` for examples.
