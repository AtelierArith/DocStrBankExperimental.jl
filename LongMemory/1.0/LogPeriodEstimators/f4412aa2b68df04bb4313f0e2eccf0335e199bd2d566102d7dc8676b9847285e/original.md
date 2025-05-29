```
periodogram_plot(x::Array; slope::Bool=true)
```

Plots the log-periodogram of a time series `x`.

# Arguments

  * `x::Vector`: time series

# Output

  * `p1::Plots.Plot`: log-periodogram

# Optional arguments

  * `slope::Bool`: If true, the slope of the linear regression is displayed.

# Examples

```julia-repl
julia> periodogram_plot(randn(100,1))
```
