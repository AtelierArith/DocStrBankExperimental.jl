```
plsqda(; kwargs...)
plsqda(X, y; kwargs...)
plsqda(X, y, weights::Weight; kwargs...)
```

QDA on PLS latent variables (PLS-QDA) with continuum.

  * `X` : X-data (n, p).
  * `y` : Univariate class membership (n).
  * `weights` : Weights (n) of the observations. Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. latent variables (LVs) to compute. Must be >= 1.
  * `prior` : Type of prior probabilities for class membership. Possible values are: `:prop` (proportionnal),    `:unif` (uniform), or a vector (of length equal to the number of classes) giving the prior weight for each class    (in case of vector, it must be sorted in the same order as `mlev(y)`).
  * `alpha` : Scalar (∈ [0, 1]) defining the continuum between QDA (`alpha = 0`) and LDA (`alpha = 1`).
  * `scal` : Boolean. If `true`, each column of `X` and Ydummy is scaled by its uncorrected standard deviation   in the PLS computation.

QDA on PLS latent variables. The approach is as follows:

1. The training variable `y` (univariate class membership) is transformed to a dummy table (Ydummy)   containing nlev columns, where nlev is the number of classes present in `y`. Each column of   Ydummy is a dummy (0/1) variable.
2. A multivariate PLSR (PLSR2) is run on {`X`, Ydummy}, returning a score matrix `T`.
3. A QDA (possibly with continuum) is done on {`T`, `y`}, returning estimates of posterior probabilities (∊ [0, 1])   of class membership.
4. For a given observation, the final prediction is the class corresponding to the dummy variable for which   the probability estimate is the highest.

The low-level method (i.e. having argument `weights`) of the function allows to set any vector of observation weights  to be used in the intermediate computations. In the high-level methods (no argument `weights`), they are automatically  computed from the argument `prior` value: for each class, the total of the observation weights is set equal to  the prior probability corresponding to the class.

**Note:** For highly unbalanced classes, it may be recommended to set 'prior = :unif' when using the function (and to use a score such as `merrp` instead of `errp` when evaluating the perfomance).

See function `plslda` for examples.
