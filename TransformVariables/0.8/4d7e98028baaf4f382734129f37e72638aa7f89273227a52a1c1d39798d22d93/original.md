```
CorrCholeskyFactor(n)
```

!!! note
    It is better style to use [`corr_cholesky_factor`](@ref), this will be deprecated.


Cholesky factor of a correlation matrix of size `n`.

Transforms $n×(n-1)/2$ real numbers to an $n×n$ upper-triangular matrix `U`, such that `U'*U` is a correlation matrix (positive definite, with unit diagonal).

# Notes

If

  * `z` is a vector of `n` IID standard normal variates,
  * `σ` is an `n`-element vector of standard deviations,
  * `U` is obtained from `CorrCholeskyFactor(n)`,

then `Diagonal(σ) * U' * z` will be a multivariate normal with the given variances and correlation matrix `U' * U`.
