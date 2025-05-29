```julia
get_time_series_multiple(
    data::InfrastructureSystems.SystemData;
    ...
) -> Channel{Any}
get_time_series_multiple(
    data::InfrastructureSystems.SystemData,
    filter_func;
    type,
    name
) -> Channel{Any}

```

Returns an iterator of `TimeSeriesData` instances attached to the system.

Note that passing a filter function can be much slower than the other filtering parameters because it reads time series data from media.

Call `collect` on the result to get an array.

# Arguments

  * `data::SystemData`: system
  * `filter_func = nothing`: Only return time_series for which this returns true.
  * `type = nothing`: Only return time_series with this type.
  * `name = nothing`: Only return time_series matching this value.

See also: [`get_time_series_multiple` from an individual component or attribute](@ref get_time_series_multiple(     owner::TimeSeriesOwners,     filter_func = nothing;     type = nothing,     name = nothing, ))
