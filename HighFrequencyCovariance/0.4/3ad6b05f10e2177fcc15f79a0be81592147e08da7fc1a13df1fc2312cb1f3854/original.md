```
identity_regularisation(mat::Hermitian, identity_weight::Real)
```

Regularisation of the correlation matrix by mixing with the identity matrix.

### Inputs

  * `mat` - A matrix to be regularised.
  * `identity_weight` - How much weight to give to the identity matrix. Should be between 0 and 1.

### Returns

  * A `Hermitian`.

```
identity_regularisation(mat::Hermitian, asset_returns::DataFrame)
```

Regularisation of the correlation matrix by mixing with the identity matrix as per Ledoit & Wolf 2003.

### Inputs

  * `mat` - A matrix to be regularised.
  * `ts` - Tick data.

### Returns

  * A `Hermitian`.

    identity*regularisation(       mat::Hermitian,       ts::SortedDataFrame,       mat*labels::Vector;       spacing::Union{Missing,<:Real} = missing,   )

Regularisation of the correlation matrix by mixing with the identity matrix as per Ledoit & Wolf 2003.

### Inputs

  * `mat` - A matrix to be regularised.
  * `ts` - Tick data.
  * `mat_labels` - The labels for each asset in the matrix.
  * `spacing` A spacing to use to estimate returns. This is used in determining the optimal weight to give to the identity matrix.

### Returns

  * A `Hermitian`.

    identity*regularisation(       covariance*matrix::CovarianceMatrix,       ts::SortedDataFrame;       spacing::Union{Missing,<:Real} = missing,       apply*to*covariance::Bool = true,   )

Regularisation of the correlation matrix by mixing with the identity matrix as per Ledoit & Wolf 2003.

### Inputs

  * `covariance_matrix` - The `CovarianceMatrix` to be regularised.
  * `ts` - Tick data.
  * `spacing` A spacing to use to estimate returns. This is used in determining the optimal weight to give to the identity matrix.
  * `apply_to_covariance` Should regularisation be applied to the covariance matrix or the correlation matrix.

### Returns

  * A `CovarianceMatrix`.

    identity*regularisation(       covariance*matrix::CovarianceMatrix,       identity*weight::Real;       apply*to_covariance = false,   )

Regularisation of the correlation matrix by mixing with the identity matrix.

### Inputs

  * `covariance_matrix` - The `CovarianceMatrix` to be regularised.
  * `identity_weight` - How much weight to give to the identity matrix. Should be between 0 and 1.
  * `apply_to_covariance` Should regularisation be applied to the covariance matrix or the correlation matrix.

### Returns

  * A `CovarianceMatrix`.

### References

Ledoit, O. , Wolf, M. 2003. Improved Estimation of the Covariance Matrix of Stock Returns with an application to portfolio selection. Journal of empirical finance. 10. 603-621.
