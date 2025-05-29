```
cov_to_cor(mat::AbstractMatrix)
```

Converts a matrix (representing a covariance matrix) into a `Hermitian` correlation matrix and a vector of standard deviations.

### Inputs

  * `cor` - A matrix.

### Returns

  * A `Hermitian`.
  * A `Vector` of standard deviations (not volatilities).
