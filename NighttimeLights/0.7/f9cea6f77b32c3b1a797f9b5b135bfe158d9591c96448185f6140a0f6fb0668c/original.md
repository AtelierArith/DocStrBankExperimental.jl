```
readnl(xlims = X(Rasters.Between(65.39, 99.94)), ylims = Y(Rasters.Between(5.34, 39.27)), start_date = Date(2012, 04), end_date = Date(2023, 01))
```

Read nighttime lights data from a specific directory and return two raster series representing radiance and coverage.

# Arguments

  * `xlims`: An instance of `X(Rasters.Between(min, max))`, defining the X-coordinate limits. Default is `X(Rasters.Between(65.39, 99.94))`.
  * `ylims`: An instance of `Y(Rasters.Between(min, max))`, defining the Y-coordinate limits. Default is `Y(Rasters.Between(5.34, 39.27))`.
  * `start_date`: The start date (inclusive) of the period for which to load data. Should be an instance of `Date`. Default is `Date(2012, 04)`.
  * `end_date`: The end date (inclusive) of the period for which to load data. Should be an instance of `Date`. Default is `Date(2023, 01)`.

# Returns

Two data cubes. The first contains the radiance data, and the second contains the coverage data. Each data cube includes data from the start*date to the end*date, sorted in ascending order.

# Examples

```julia using Rasters xlims = X(Rasters.Between(65.39, 75.39)) ylims = Y(Rasters.Between(5.34, 15.34)) start*date = Date(2015, 01) end*date = Date(2020, 12) rad*dc, cf*dc = readnl(xlims, ylims, start*date, end*date)
