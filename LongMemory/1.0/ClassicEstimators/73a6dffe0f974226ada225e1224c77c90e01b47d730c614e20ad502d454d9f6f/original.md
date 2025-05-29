```
autocorrelation_plot(x::Array, k::Int)
```

Computes the autocorrelation function of a time series.

# Arguments

  * `x::Array`: The time series.
  * `k::Int`: The lag of the autocorrelation.

# Output

  * `p1::Plots.Plot`: The autocorrelation function.

# Examples

```julia
julia> autocorrelation_plot(randn(100), 10)
```
