Package: ForecastPlots

```
dplot(x; dlabels = ["Data","Trend","Seasonal","Remainder"])
```

Plot a seasonal, trend and remainder decomposition of a time series.

# Arguments

  * `x`: Matrix with three columns containing sesonality, trend and remainder decomposition
  * `dlabels`: String array of length four containing labels for data, seasonality, trend and remainder.

# Returns

Sesonal decomposition plot with scale bars

# Examples

```julia-repl
dplot(randn(100,3))
dplot(randn(100,3); labels = ["數據","趨勢","季節性","剩餘"])
dplot(rand(100,3),now()-Day(99):Day(1):now())
```
