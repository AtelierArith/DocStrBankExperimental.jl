```
fdasvd(; kwargs...)
fdasvd(X, y, weights; kwargs...)
fdasvd!(X::Matrix, y, weights; kwargs...)
```

Factorial discriminant analysis (FDA).

  * `X` : X-data (n, p).
  * `y` : y-data (n) (class membership).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. of discriminant components.
  * `lb` : Ridge regularization parameter "lambda".   Can be used when `X` has collinearities.
  * `prior` : Type of prior probabilities for class    membership. Possible values are: `:unif` (uniform),    `:prop` (proportional), or a vector (of length equal to    the number of classes) giving the prior weight for each class    (in case of vector, it must be sorted in the same order as `mlev(y)`).
  * `scal` : Boolean. If `true`, each column of `X`    is scaled by its uncorrected standard deviation.

FDA by a weighted SVD factorization of the matrix of the class centers  (after spherical transformaton). The function gives the same results as  function `fda`.

See function `fda` for details and examples.
