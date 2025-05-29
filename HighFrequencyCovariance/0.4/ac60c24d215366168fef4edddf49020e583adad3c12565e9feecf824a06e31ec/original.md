```
valid_correlation_matrix(mat::Hermitian, min_eigen_threshold::Real = 0.0)

valid_correlation_matrix(covar::CovarianceMatrix, min_eigen_threshold::Real = 0.0)
```

Test if a `Hermitian` matrix is a valid correlation matrix. This is done by testing if it is psd, if it has a unit diagonal and if all other elements are less than one. If a `Hermitian` is input then it will be tested. If a `CovarianceMatrix` is input then its correlation matrix will be tested.

### Inputs

  * `mat` - A `Hermitian` matrix or a `CovarianceMatrix`
  * `min_eigen_threshold` - How big does the smallest eigenvalue have to be.

### Returns

  * A `Bool` that is true if mat is a valid correlation matrix and false if not.
