```
acweuler(lags, acf; dims=ndims(acf))
```

Compute the ACW at 1/e (≈ 0.368) along specified dimension.

# Arguments

  * `lags::AbstractVector{T}`: Vector of lag values
  * `acf::AbstractArray{S}`: Array of autocorrelation values
  * `dims::Int=ndims(acf)`: Dimension along which to compute

# Returns

  * First lag where autocorrelation falls below 1/e

# Notes

  * For exponential decay, equals the timescale parameter tau
