```
cov_to_cor_and_vol(
    mat::AbstractMatrix,
    duration_of_covariance_matrix::Dates.Period,
    duration_for_desired_vols::Dates.Period,
)

cov_to_cor_and_vol(
    mat::AbstractMatrix,
    duration_of_covariance_matrix::Real,
    duration_for_desired_vols::Real,
)
```

Converts a matrix (representing a covariance matrix) into a `Hermitian` correlation matrix and a vector of volatilities.

### Inputs

  * `cor` - A correlation matrix.
  * `duration_of_covariance_matrix` - The duration of the covariance matrix. If these are input as reals they must have the same units.
  * `duration_for_desired_vols` - The duration you want a volatility for. If these are input as reals they must have the same units.

### Returns

  * A `Hermitian`.
  * A `Vector` of volatilities.

    cov*to*cor*and*vol(       mat::AbstractMatrix,       duration*of*covariance*matrix*in*natural*units::Real,   )

### Inputs

  * `cor` - A correlation matrix.
  * `duration_of_covariance_matrix_in_natural_units` - The duration of the covariance matrix. It duration must be input in units that you know of (for instance the `time_period_per_unit` of a `SortedDataFrame`).

### Returns

  * A `Hermitian`.
  * A `Vector` of volatilities.
