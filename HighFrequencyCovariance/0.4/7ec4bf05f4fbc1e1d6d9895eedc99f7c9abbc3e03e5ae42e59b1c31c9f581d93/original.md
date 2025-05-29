```
nearest_correlation_matrix(
    mat::AbstractMatrix,
    weighting_matrix::Union{Diagonal,Hermitian} = Diagonal(Float64.(I(size(mat)[1])));
    doDykstra::Bool = true,
    stop_at_first_correlation_matrix::Bool = true,
    max_iterates::Integer = 1000,
)
```

Maps a matrix to the nearest valid correlation matrix (pdf matrix with unit diagonal and all other entries below 1 in absolute value).

### Inputs

  * `mat` - A matrix you want to regularise.
  * `ts` - The tick data.
  * `weighting_matrix` - The weighting matrix used to weight what the **nearest** valid correlation matrix is.
  * `doDykstra` - Should Dykstra correction be done.
  * `stop_at_first_correlation_matrix` - Should we keep iterating until we have done all iterates or stop at the first valid correlation matrix.
  * `max_iterates` - The maximum number of iterates to do towards a valid correlation matrix.

### Returns

  * A `Matrix`
  * An integer saying how many iterates were done
  * A Symbol with a convergence message.

    nearest*correlation*matrix(       covariance*matrix::CovarianceMatrix,       ts::SortedDataFrame;       weighting*matrix::Union{Diagonal,Hermitian} = Diagonal(eltype(covariance*matrix.correlation).(I(size(covariance*matrix.correlation)[1]))),       doDykstra::Bool = true,       stop*at*first*correlation*matrix::Bool = true,       max_iterates::Integer = 1000,   )

Maps a matrix to the nearest valid correlation matrix (pdf matrix with unit diagonal and all other entries below 1 in absolute value).

### Inputs

  * `covariance_matrix` - The matrix you want to regularise.
  * `ts` - The tick data.
  * `weighting_matrix` - The weighting matrix used to weight what the **nearest** valid correlation matrix is.
  * `doDykstra` - Should Dykstra correction be done.
  * `stop_at_first_correlation_matrix` - Should we keep iterating until we have done all iterates or stop at the first valid correlation matrix.
  * `max_iterates` - The maximum number of iterates to do towards a valid correlation matrix.

### Returns

  * A `CovarianceMatrix`

    nearest*correlation*matrix(       covariance*matrix::CovarianceMatrix;       weighting*matrix::Union{Diagonal,Hermitian} = Diagonal(eltype(covariance*matrix.correlation).(I(size(covariance*matrix.correlation)[1]))),       doDykstra::Bool = true,       stop*at*first*correlation*matrix::Bool = true,       max_iterates::Integer = 1000,   )

Maps a matrix to the nearest valid correlation matrix (pdf matrix with unit diagonal and all other entries below 1 in absolute value).

### Inputs

  * `covariance_matrix` - The matrix you want to regularise.
  * `weighting_matrix` - The weighting matrix used to weight what the **nearest** valid correlation matrix is.
  * `doDykstra` - Should Dykstra correction be done.
  * `stop_at_first_correlation_matrix` - Should we keep iterating until we have done all iterates or stop at the first valid correlation matrix.
  * `max_iterates` - The maximum number of iterates to do towards a valid correlation matrix.

### Returns

  * A `CovarianceMatrix`

    nearest*correlation*matrix(       mat::Hermitian,       ts::SortedDataFrame;       weighting*matrix::Union{Diagonal,Hermitian} = Diagonal(eltype(mat).(I(size(mat)[1]))),       doDykstra::Bool = true,       stop*at*first*correlation*matrix::Bool = true,       max*iterates::Integer = 1000,   )

Maps a matrix to the nearest valid correlation matrix (pdf matrix with unit diagonal and all other entries below 1 in absolute value).

### Inputs

  * `mat` - The matrix you want to regularise.
  * `weighting_matrix` - The weighting matrix used to weight what the **nearest** valid correlation matrix is.
  * `doDykstra` - Should Dykstra correction be done.
  * `stop_at_first_correlation_matrix` - Should we keep iterating until we have done all iterates or stop at the first valid correlation matrix.
  * `max_iterates` - The maximum number of iterates to do towards a valid correlation matrix.

### Returns

  * A `Hermitian`

    nearest*correlation*matrix(      mat::Hermitian;      weighting*matrix::Union{Diagonal,Hermitian} = Diagonal(eltype(mat).(I(size(mat)[1]))),      doDykstra::Bool = true,      stop*at*first*correlation*matrix::Bool = true,      max*iterates::Integer = 1000,   )

Maps a matrix to the nearest valid correlation matrix (pdf matrix with unit diagonal and all other entries below 1 in absolute value).

### Inputs

  * `covariance_matrix` - The matrix you want to regularise.
  * `ts` - The tick data.
  * `weighting_matrix` - The weighting matrix used to weight what the **nearest** valid correlation matrix is.
  * `doDykstra` - Should Dykstra correction be done.
  * `stop_at_first_correlation_matrix` - Should we keep iterating until we have done all iterates or stop at the first valid correlation matrix.
  * `max_iterates` - The maximum number of iterates to do towards a valid correlation matrix.

### Returns

  * A `Hermitian`

### References

Higham NJ (2002). "Computing the nearest correlation matrix - a problem from finance." IMA Journal of Numerical Analysis, 22, 329–343. doi:10.1002/nla.258.
