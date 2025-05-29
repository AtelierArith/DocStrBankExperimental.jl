```
seriesoverlay(ts1, ts2)
```

Return a new [`TSeries`](@ref) over the full range of both arguments. The overlapping part contains values from the last argument.

!!! note "Deprecation Note"
    This function will be removed in the future. Use [`TimeSeriesEcon.overlay`](@ref) instead. Note the important difference that in [`TimeSeriesEcon.overlay`](@ref) the values in the overlay come from the *first* series where the value exists, as opposed to `seriesoverlay` where it was from the last one.


See also: [`dictoverlay`](@ref)
