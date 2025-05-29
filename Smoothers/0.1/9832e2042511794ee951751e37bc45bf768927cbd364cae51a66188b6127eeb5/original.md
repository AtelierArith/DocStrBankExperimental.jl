Package: Forecast

```
hma(x, n)
```

Applies the Henderson moving average filter to dataset `x` with `n`-term.

"Henderson moving averages are filters which were derived by Robert Henderson in 1916  for use in actuarial applications. They are trend filters, commonly used in time series  analysis to smooth seasonally adjusted estimates in order to generate a trend estimate.

They are used in preference to simpler moving averages because they can reproduce  polynomials of up to degree 3, thereby capturing trend turning points.

The ABS uses Henderson moving averages to produce trend estimates from a seasonally  adjusted series. The trend estimates published by the ABS are typically derived using  a 13 term Henderson filter for monthly series, and a 7 term Henderson filter for quarterly series.

Henderson filters can be either symmetric or asymmetric. Symmetric moving averages can be applied  at points which are sufficiently far away from the ends of a time series. In this case, the  smoothed value for a given point in the time series is calculated from an equal number of values  on either side of the data point." - Australian Bureau of Statistics (www.abs.gov.au)

# Arguments

  * `x`: Observations' support.
  * `n`: Observation values, tipically 13 or 7 for quarterly data.

# Returns

An array of Henderson filter smoothed values provided in `s`.

# Examples

```julia-repl
julia> hma(rand(1000), 303)
1000-element Vector{Float64}}:
[...]
```
