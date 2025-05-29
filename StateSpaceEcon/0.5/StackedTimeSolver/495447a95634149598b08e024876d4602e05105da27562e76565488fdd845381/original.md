```
dictoverlay(d1, d2)
```

Merge two dictionaries. Common key where the values are [`TSeries`](@ref TimeSeriesEcon.TSeries) of the same frequency are overlayed. Otherwise, a common key takes the value of the last Dict containing it.

!!! note "Deprecation Note"
    This function will be removed. Use [`TimeSeriesEcon.overlay`](@ref) instead. An important difference is that [`TimeSeriesEcon.overlay`](@ref) keeps the values from the first argument where the key appears, while `dictoverlay` keeps it from the last.

