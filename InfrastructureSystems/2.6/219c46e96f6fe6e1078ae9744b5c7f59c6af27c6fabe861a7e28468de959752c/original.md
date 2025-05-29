```julia
get_next_time_series_array!(
    cache::InfrastructureSystems.TimeSeriesCache
) -> Any

```

Return the next TimeSeries.TimeArray.

Returns `nothing` when all data has been read. Call [`reset!`](@ref) to restart. Call [`get_next_time`](@ref) to check the start time.

Reads from storage if the data is not already in cache.

# Arguments

  * `cache::StaticTimeSeriesCache`: cached instance

# Examples

```julia
cache = ForecastCache(Deterministic, component, "max_active_power")
window1 = get_next_time_series_array!(cache)
window2 = get_next_time_series_array!(cache)
```
