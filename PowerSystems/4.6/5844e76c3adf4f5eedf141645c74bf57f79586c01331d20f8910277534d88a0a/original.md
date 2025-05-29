```julia
get_time_series_multiple(
    sys::PowerSystems.System;
    ...
) -> Channel{Any}
get_time_series_multiple(
    sys::PowerSystems.System,
    filter_func;
    type,
    name
) -> Channel{Any}

```

Return an iterator of time series in order of initial time.

Note that passing a filter function can be much slower than the other filtering parameters because it reads time series data from media.

Call `collect` on the result to get an array.

# Arguments

  * `data::SystemData`: system
  * `filter_func = nothing`: Only return time series for which this returns true.
  * `type = nothing`: Only return time series with this type.
  * `name = nothing`: Only return time series matching this value.

# Examples

```julia
for time_series in get_time_series_multiple(sys)
    @show time_series
end

ts = collect(get_time_series_multiple(sys; type = SingleTimeSeries))
```
