```
is_psd_matrix(mat::Hermitian, min_eigen_threshold::Real = 0.0)

is_psd_matrix(covar::CovarianceMatrix)
```

Test if a matrix is psd (Positive Semi-Definite). This is done by seeing if all eigenvalues are positive. If a `Hermitian` is input then it will be tested. If a `CovarianceMatrix` is input then its correlation matrix will be tested.

### Inputs

  * `mat` - A `Hermitian` matrix or a `CovarianceMatrix`
  * `min_eigen_threshold` - How big does the smallest eigenvalue have to be.

### Returns

  * A `Bool` that is true if mat is psd and false if not.
