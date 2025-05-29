```
struct ParameterTimeseriesIndex
function ParameterTimeseriesIndex(timeseries_idx, parameter_idx)
```

A struct storing the index of the timeseries of a timeseries parameter in a parameter timeseries object. `timeseries_idx` refers to an index that identifies the timeseries that the parameter belongs to. `parameter_idx` refers to the index of the parameter's timeseries in that timeseries object. Note that `parameter_idx` may be different from the object returned by [`parameter_index`](@ref) for a given parameter. The two fields in this struct are `timeseries_idx` and `parameter_idx`.
