```
get_correlation(covar::CovarianceMatrix, asset1::Symbol, asset2::Symbol)
```

Extract the correlation between two assets stored in a CovarianceMatrix.

### Inputs

  * `covar` - A `CovarianceMatrix`
  * `asset1` - A `Symbol` representing an asset.
  * `asset2` - A `Symbol` representing an asset.

### Returns

  * A Scalar (the correlation coefficient).
