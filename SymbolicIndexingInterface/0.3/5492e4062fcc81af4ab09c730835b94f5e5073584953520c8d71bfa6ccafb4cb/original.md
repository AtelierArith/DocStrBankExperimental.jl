```
timeseries_parameter_index(indp, sym)
```

Return the index of timeseries parameter `sym` in `indp`. Must return this index as a [`ParameterTimeseriesIndex`](@ref) object. Return `nothing` if `sym` is not a timeseries parameter in `indp`. Defaults to returning `nothing`. Respects the [`symbolic_container`](@ref) fallback for `indp` if present.
