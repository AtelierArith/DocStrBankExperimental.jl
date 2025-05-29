```
comp_cc(data1::AbstractArray{T}, data2::AbstractArray{T}, max_lag::Integer;
       dims::Int=ndims(data1)) where {T <: Real}
```

Compute cross-correlation between two arrays along specified dimension.

# Arguments

  * `data1`: First array of time series data
  * `data2`: Second array of time series data
  * `max_lag`: Maximum lag to compute
  * `dims`: Dimension along which to compute cross-correlation (defaults to last dimension)

# Returns

Array with cross-correlation values, reduced along specified dimension
