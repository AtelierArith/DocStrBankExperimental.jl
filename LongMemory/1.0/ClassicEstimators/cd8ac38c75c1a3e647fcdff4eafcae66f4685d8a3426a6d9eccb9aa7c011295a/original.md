```
autocorrelation(x::Array, k::Int; flag::Bool=false)
```

Computes the autocorrelation function of a time series.

# Arguments

  * `x::Array`: The time series.
  * `k::Int`: The lag of the autocorrelation.

# Output

  * `acf::Array`: The autocorrelation function.

# Optional arguments

  * `flag::Bool`: If true, the autocorrelation function is displayed.

# Examples

```julia
julia> autocorrelation(randn(100), 10)
```
