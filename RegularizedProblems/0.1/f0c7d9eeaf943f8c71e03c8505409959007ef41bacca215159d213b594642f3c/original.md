```
model, nls_model, sol = random_matrix_completion_model(; kwargs...)
```

Return an instance of an `NLPModel` and an instance of an `NLSModel` representing the same matrix completion problem, i.e., the square linear least-squares objective

½ ‖P(X - A)‖²

in the Frobenius norm, where X is the unknown image represented as an m x n matrix, A is a fixed image, and the operator P only retains a certain subset of pixels of X and A.

## Keyword Arguments

  * `m :: Int`: the number of rows of X and A (default: 100)
  * `n :: Int`: the number of columns of X and A (default: 100)
  * `r :: Int`: the desired rank of A (default: 5)
  * `sr :: AbstractFloat`: a threshold between 0 and 1 used to determine the set of pixels

retained by the operator P (default: 0.8)

  * `va :: AbstractFloat`: the variance of a first Gaussian perturbation to be applied to A (default: 1.0e-4)
  * `vb :: AbstractFloat`: the variance of a second Gaussian perturbation to be applied to A (default: 1.0e-2)
  * `c :: AbstractFloat`: the coefficient of the convex combination of the two Gaussian perturbations (default: 0.2).

## Return Value

An instance of a `FirstOrderModel` and of a `FirstOrderNLSModel` that represent the same matrix completion problem, and the exact solution.
