```
cor_to_cov(cor::AbstractMatrix,sdevs::Vector{<:Real})
```

Converts a correlation matrix and some standard deviations into a `Hermitian` covariance matrix.

### Inputs

  * `cor` - A correlation matrix.
  * `sdevs` - A vector of standard deviations (not volatilities).

### Returns

  * A `Hermitian`.
