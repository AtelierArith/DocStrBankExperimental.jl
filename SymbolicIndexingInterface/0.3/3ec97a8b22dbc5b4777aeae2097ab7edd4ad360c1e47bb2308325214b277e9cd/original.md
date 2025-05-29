```
get_all_timeseries_indexes(indp, sym)
```

Return a `Set` of all unique timeseries indexes of variables in symbolic variable `sym`. `sym` may be a symbolic variable or expression, an array of symbolics, an index, or an array of indices. Continuous variables correspond to the [`ContinuousTimeseries`](@ref) timeseries index. Non-timeseries parameters do not have a timeseries index. Timeseries parameters have the same timeseries index as that returned by [`timeseries_parameter_index`](@ref). Note that the independent variable corresponds to the `ContinuousTimeseries` timeseries index.

Any ambiguities should be resolved in favor of variables. For example, if `1` could refer to the variable at index `1` or parameter at index `1`, it should be interpreted as the variable.

By default, this function returns `Set([ContinuousTimeseries()])`.
