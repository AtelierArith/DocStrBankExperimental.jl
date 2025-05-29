```
regularise(
    mat::Hermitian,
    ts::SortedDataFrame,
    mat_labels::Vector,
    method::Symbol = :correlation_default;
    spacing::Union{Missing,<:Real} = missing,
    weighting_matrix = Diagonal(eltype(mat).(I(size(mat)[1]))),
    doDykstra = true,
    stop_at_first_correlation_matrix = true,
    max_iterates = 1000,
)
```

This is a convenience wrapper for the regularisation techniques.

### General Inputs

  * `mat` - The matrix you want to regularise.
  * `ts` - The tick data.
  * `mat_labels` - The name of the assets for each row/column of the matrix.
  * `method`  - The method you want to use. This can be `:identity_regularisation`, `:eigenvalue_clean`, `:nearest_correlation_matrix` or `:nearest_psd_matrix`. You can also choose `:covariance_default` (which is `:nearest_psd_matrix`) or  `:correlation_default` (which is `:nearest_correlation_matrix`).

#### Inputs only used in `:identity_regularisation` method.

  * `spacing` - The interval spacing used in choosing an identity weight (`identity_regularisation` method only).

#### Inputs only used in `:nearest_correlation_matrix` method.

  * `weighting_matrix` - The weighting matrix used to calculate the nearest psd matrix (`:nearest_correlation_matrix` method only).
  * `doDykstra` - Should a Dykstra correction be applied (`:nearest_correlation_matrix` method only).
  * `stop_at_first_correlation_matrix` - Should we stop at first valid correlation matrix (`:nearest_correlation_matrix` method only).
  * `max_iterates` - Maximum number of iterates (`:nearest_correlation_matrix` method only).

### Returns

  * A `Hermitian`

    regularise(      covariance*matrix::CovarianceMatrix,      ts::SortedDataFrame,      method::Symbol = :nearest*correlation*matrix;      apply*to*covariance::Bool = true,      spacing::Union{Missing,<:Real} = missing,      weighting*matrix = Diagonal(eltype(covariance*matrix.correlation).(I(size(covariance*matrix.correlation)[1]))),      doDykstra = true,      stop*at*first*correlation*matrix = true,      max_iterates = 1000,   )

This is a convenience wrapper for the regularisation techniques.

### General Inputs

  * `covariance_matrix` - The matrix you want to regularise.
  * `ts` - The tick data.
  * `method`  - The method you want to use. This can be `:identity_regularisation`, `:eigenvalue_clean`, `:nearest_correlation_matrix` or `:nearest_psd_matrix`. You can also choose `:covariance_default` (which is `:nearest_psd_matrix`) or  `:correlation_default` (which is `:nearest_correlation_matrix`).
  * `apply_to_covariance` - Should regularisation be applied to the covariance matrix. If false it is applied to the correlation matrix.

#### Inputs only used in `:identity_regularisation` method.

  * `spacing` - The interval spacing used in choosing an identity weight (`identity_regularisation` method only).

#### Inputs only used in `:nearest_correlation_matrix` method.

  * `weighting_matrix` - The weighting matrix used to calculate the nearest psd matrix (`:nearest_correlation_matrix` method only).
  * `doDykstra` - Should a Dykstra correction be applied (`:nearest_correlation_matrix` method only).
  * `stop_at_first_correlation_matrix` - Should we stop at first valid correlation matrix (`:nearest_correlation_matrix` method only).
  * `max_iterates` - Maximum number of iterates (`:nearest_correlation_matrix` method only).

### Returns

  * A `CovarianceMatrix`
