```
cornerplot(data; kwargs...)
```

Takes a nSamples-by-nDimensions array, and makes density plots of every combination of the dimensions. Plots as a triangular matrix of subplots showing the correlation among input variables. Input `data` can be a MxN matrix, a `GMTdataset` or a file name that upon reading with `gmtread` returns a `GMTdataset`.

The plot consists of histograms of each column along the diagonal and scatter or hexagonal bining plots for the inter-variable relations, depending on if the the number of samples is <= 1000. But this can be changed with options in `kwargs`.

  * `cornerplot(data)`: plots every 2D projection of a multidimensional data set.
  * `cornerplot(..., varnames)`: prints the names of each dimension. `varnames` is a vector of strings  of length nDimensions. If not provided, column names in the `GMTdaset` are used.
  * `cornerplot(..., truths)`: indicates reference values on the plots.
  * `cornerplot(..., quantile)`: list of fractional quantiles to show on the 1-D histograms as vertical dashed lines.
  * `cornerplot(..., hexbin=true)`: Force hexbin plots even when number of points <= 1000.
  * `cornerplot(..., scatter=true)`: Force scatter plots even when number of points > 1000.
  * `cornerplot(..., histcolor|histfill=color)`: To paint diagonal histograms witha selected color (histcolor=:none to no paint).

Several more options in `kwargs` can be used to control plot details (and are passed to the `subplot`, `binstats` and `plot` functions.)

Example:     cornerplot(randn(2500,3), cmap=:viridis, show=1)
