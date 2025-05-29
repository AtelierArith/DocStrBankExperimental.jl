```
CorrCholesky(n)
```

Cholesky factor of a correlation matrix of size `n`. Transforms $n(n-1)/2$ real numbers to an $n×n$ lower-triangular matrix `L`, such that `L*L'` is a correlation matrix (positive definite, with unit diagonal).

# Notes

If

  * `z` is a vector of `n` IID standard normal variates,
  * `σ` is an `n`-element vector of standard deviations,
  * `C` is obtained from `CorrCholesky(n)`,

then `Diagonal(σ) * C.L * z` is a zero-centered multivariate normal variate with the standard deviations `σ` and correlation matrix `C.L * C.U`.
