```
timedata_operation(f::Function, x, y)
```

Perform `f` element-wise for potentially `TimeSeries`, `TimePattern`, or ``Map` arguments `x` and `y`.

If both `x` and `y` are either `TimeSeries` or `TimePattern`, the timestamps of `x` and `y` are combined, and both time-dependent data are sampled on each timestamps to perform the desired operation. If either `ts1` or `ts2` are `TimeSeries`, returns a `TimeSeries`. If either `ts1` or `ts2` has the `ignore_year` or `repeat` flags set to `true`, so does the resulting `TimeSeries`. For `Map`s, perform recursion until non-map operands are found.

NOTE! Currently, `Map-Map` operations require that `Map` indexes are identical!
