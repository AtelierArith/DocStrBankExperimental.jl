```
eigenvalue_clean(
    eigenvalues::Vector{<:Real},
    eigenvectors::Matrix{<:Real},
    eigenvalue_threshold::Real,
)
```

This takes the small eigenvalues (with values below eigenvalue*threshold). It sets them to the greater of their average or eigenvalue*threshold/(4*number*of*small_eigens). Then the matrix is reconstructed and returned (as a `Hermitian`)

### Inputs

  * `eigenvalues` - The eigenvalues of a matrix.
  * `eigenvectors` - The eigenvectors  of a matrix.
  * `eigenvalue_threshold` - The threshold for a eigenvalue to be altered.

### Returns

  * A `Hermitian`.

    eigenvalue*clean(mat::Hermitian, eigenvalue*threshold::Real)

This splits a matrix into its eigenvalues and eigenvectors. Then takes the small eigenvalues (with values below `eigenvalue_threshold`). It sets them to the greater of their average or `eigenvalue_threshold/(4*number_of_small_eigens)`. Then the matrix is reconstructed and returned (as a `Hermitian`)

### Inputs

  * `mat` - A matrix that you want to regularise with eigenvalue regularisation.
  * `eigenvalue_threshold` - The threshold for a eigenvalue to be altered.

### Returns

  * A `Hermitian`.

    eigenvalue_clean(mat::Hermitian, ts::SortedDataFrame)

Similarly to the above two methods these functions regularise a matrix by setting small eigenvalues to near zero. The method of Laloux, Cizeau, Bouchaud & Potters 2000 is used to choose a threshold.

### Inputs

  * `mat` - A matrix that you want to regularise with eigenvalue regularisation.
  * `ts` - The tick data.

### Returns

  * A `Hermitian`.

    eigenvalue*clean(       covariance*matrix::CovarianceMatrix,       ts::SortedDataFrame;       apply*to*covariance::Bool = true,   )

### Inputs

  * `mat` - A matrix that you want to regularise with eigenvalue regularisation.
  * `ts` - The tick data.
  * `apply_to_covariance` Should regularisation be applied to the covariance matrix or the correlation matrix.

### Returns

  * A `CovarianceMatrix`.

Note that if the input matrices include any NaN terms then regularisation is not possible. The matrix will be silently returned (as these NaNs will generally be from upstream problems so it is useful to return the matrix rather than throw at this point).As a result outputs should be checked.

## References

Laloux, L., Cizeau, P., Bouchaud J. , Potters, M. 2000. "Random matrix theory and financial correlations" International Journal of Theoretical Applied FInance, 3, 391-397.
