```
nearest_psd_matrix(mat::Hermitian)
```

This function maps a Hermitian matrix to the nearest psd matrix. This uses the `project_to_S` method in Higham (2001; Theorem 3.2). No special weighting is applied in this case. Advanced users can use the `project_to_S` directly if they want to use weights in order to decide what the `closest` pds matrix.

### Inputs

  * `mat` - The matrix you want to map to a psd matrix

### Results

  * A `Hermitian`

    nearest*psd*matrix(       covariance*matrix::CovarianceMatrix;       apply*to_covariance::Bool = true,   )

This function maps a Hermitian matrix to the nearest psd matrix. This uses the `project_to_S` method in Higham (2001; Theorem 3.2). No special weighting is applied in this case. Advanced users can use the `project_to_S` directly if they want to use weights in order to decide what the `closest` pds matrix.

### Inputs

  * `covariance_matrix` - The matrix you want to map to a psd matrix
  * `apply_to_covariance` - Should regularisation be applied to the correlation or covariance matrix.

### Results

  * A `CovarianceMatrix`

    nearest*psd*matrix(       covariance*matrix::CovarianceMatrix,       ts::SortedDataFrame;       apply*to_covariance::Bool = true,   )

This function maps a Hermitian matrix to the nearest psd matrix. This uses the `project_to_S` method in Higham (2001; Theorem 3.2). No special weighting is applied in this case. Advanced users can use the `project_to_S` directly if they want to use weights in order to decide what the `closest` pds matrix.

### Inputs

  * `covariance_matrix` - The matrix you want to map to a psd matrix
  * `ts` - The Tick data
  * `apply_to_covariance` - Should regularisation be applied to the correlation or covariance matrix.

### Results

  * A `CovarianceMatrix`

### References

Higham NJ (2002). "Computing the nearest correlation matrix - a problem from finance." IMA Journal of Numerical Analysis, 22, 329–343. doi:10.1002/nla.258.
