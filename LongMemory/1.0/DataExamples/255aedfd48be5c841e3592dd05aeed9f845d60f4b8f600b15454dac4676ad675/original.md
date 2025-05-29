```
LMPlot(x::Array;lags::Int=50,name::String="Time series")
```

Returns a plot of the time series `x`.

# Arguments

  * `x::Array`: The time series.

# Optional arguments

  * `lags::Int`: The number of lags to use in the autocorrelation function.
  * `name::String`: The name of the time series to use in the plot.

# Output

  * `pp::Plot`: Four plots are returned in a 2x2 grid: 

      * The first plot is the time series of `x`.
      * The second plot is the autocorrelation function of `x` using the `autocorrelation_plot` function.
      * The third plot is the periodogram of `x` using the `periodogram_plot` function.
      * The fourth plot is the variance plot of `x` using the `variance_plot` function.

# Examples

```julia
julia> LMPlot(randn(100))
```
