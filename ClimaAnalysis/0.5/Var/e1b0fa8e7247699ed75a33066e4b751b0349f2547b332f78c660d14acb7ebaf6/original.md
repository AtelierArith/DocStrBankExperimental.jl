```
window(var::OutputVar, dim_name; left = nothing, right = nothing)
```

Return a new OutputVar by selecting the values of the given `dim`ension that are between `left` and `right`.

If `left` and/or `right` are `nothing`, assume beginning (or end) of the array.

For the time dimension, `left` and `right` can also be `Dates.DateTime` (if `var` contains a `start_date`).

# Example

```julia
window(var, 'lat', left = -50, right = 50)
window(var, 'time', left = DateTime(2008), right = DateTime(2009))
```

!!! compat "Support for Dates and generalized dimension names"
    Calling `window` with a `DateTime` and specifying a dimension by one of its name (instead of the actual name in the file) was introduced in ClimaAnalysis v0.5.17.

