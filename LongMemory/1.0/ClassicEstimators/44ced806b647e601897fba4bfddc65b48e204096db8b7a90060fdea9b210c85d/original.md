```
sstdk(x::Array, m::Int)
```

Computes the sample standard deviation of a time series using the m-th order sample mean.

# Arguments

  * `x::Array`: The time series.
  * `m::Int`: The order of the sample mean.

# Output

  * `std::Real`: The sample standard deviation.

# Examples

```julia
julia> sstdk(randn(100), 20)
```
