```
NileDataPlot()
```

Returns a plot of the yearly Nile River minimum data from 622 to 1284.

# Output

  * `pp::Plot`: The plot of the Nile River data.
  * Four plots are returned in a 2x2 grid: 

      * The first plot is the time series of the Nile River data.
      * The second plot is the autocorrelation function of the Nile River data using the `autocorrelation_plot` function.
      * The third plot is the periodogram of the Nile River data using the `periodogram_plot` function.
      * The fourth plot is the variance plot of the Nile River data using the `variance_plot` function.

# Notes

This function uses the `NileData()` function to load the data.

# Examples

```julia
julia> NileDataPlot()
```
