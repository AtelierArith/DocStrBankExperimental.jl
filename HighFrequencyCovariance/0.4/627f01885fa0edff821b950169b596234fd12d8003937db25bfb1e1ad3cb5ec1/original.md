```
combine_covariance_matrices(
    vect::Vector{CovarianceMatrix{T}},
    cor_weights::Vector{<:Real} = repeat([1.0], length(vect)),
    vol_weights::Vector{<:Real} = cor_weights,
    time_period_per_unit::Union{Missing,Dates.Period} = vect[1].time_period_per_unit,
) where T<:Real
```

Combines a vector of `CovarianceMatrix` structs into one `CovarianceMatrix` struct.

### Inputs

  * `vect` - A vector of `CovarianceMatrix` structs.
  * `cor_weights` - A vector for how much to weight the correlations from each covariance matrix (by default they will be equalweighted).
  * `vol_weights` - A vector for how much to weight the volatilities from each covariance matrix (by default they will be equalweighted).
  * `time_period_per_unit` - What time period should the volatilities be scaled to.

### Returns

  * A matrix and a vector of labels for each row/column of the matrix.
