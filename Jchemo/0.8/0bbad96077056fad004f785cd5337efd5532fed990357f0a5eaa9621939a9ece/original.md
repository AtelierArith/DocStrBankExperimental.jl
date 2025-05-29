```
splsqda(; kwargs...)
splsqda(X, y; kwargs...)
splsqda(X, y, weights::Weight; kwargs...)
```

Sparse PLS-QDA (with continuum).

  * `X` : X-data (n, p).
  * `y` : Univariate class membership (n).
  * `weights` : Weights (n) of the observations. Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments: 

  * `nlv` : Nb. latent variables (LVs) to compute. Must be >= 1.
  * `meth` : Method used for the sparse thresholding.    Possible values are: `:soft`, `:hard`. See thereafter.
  * `nvar` : Nb. variables (`X`-columns) selected for each LV.    Can be a single integer (i.e. same nb. of variables for each LV),    or a vector of length `nlv`.
  * `prior` : Type of prior probabilities for class membership. Possible values are: `:prop` (proportionnal),    `:unif` (uniform), or a vector (of length equal to the number of classes) giving the prior weight for each class    (in case of vector, it must be sorted in the same order as `mlev(y)`).
  * `alpha` : Scalar (∈ [0, 1]) defining the continuum between QDA (`alpha = 0`) and LDA (`alpha = 1`).
  * `scal` : Boolean. If `true`, each column of `X` and Ydummy is scaled by its uncorrected standard deviation   in the PLS computation.

Same as function `plsqda` (PLSR-QDA) except that a sparse PLSR (function `splsr`), instead of a PLSR (function `plskern`),  is run on the Y-dummy table.

See function `splslda` for examples.
