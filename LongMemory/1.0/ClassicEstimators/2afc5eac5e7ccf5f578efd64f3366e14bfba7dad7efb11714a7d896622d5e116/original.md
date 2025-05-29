```
sstd(x::Array; k::Int=0)
```

Computes the sample standard deviation of a time series.

# Arguments

  * `x::Array`: The time series.

# Output

  * `std::Real`: The sample standard deviation.

# Optional arguments

  * `k::Int`: The bias-correction term.

# Notes

This function divides by T instead of T-1 if no bias-correction term is provided.

# Examples

```julia
julia> sstd(randn(100))
```
