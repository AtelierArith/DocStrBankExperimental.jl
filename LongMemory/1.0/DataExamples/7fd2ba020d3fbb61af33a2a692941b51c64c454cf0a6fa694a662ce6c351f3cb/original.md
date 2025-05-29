```
NHTempDataPlot()
```

Returns a plot of the monthly Northern Hemisphere temperature data from January 1850 to September 2023.

# Output

  * `pp::Plot`: The plot of the Nile River data.
  * Four plots are returned in a 2x2 grid: 

      * The first plot is the time series of the Northern Hemisphere temperature data.
      * The second plot is the autocorrelation function of the Northern Hemisphere temperature data using the `autocorrelation_plot` function.
      * The third plot is the periodogram of the Northern Hemisphere temperature data using the `periodogram_plot` function.
      * The fourth plot is the variance plot of the Northern Hemisphere temperature data using the `variance_plot` function.

# Notes

This function uses the `NHTempData()` function to load the data.

# Examples

```julia
julia> NHTempDataPlot()
```
