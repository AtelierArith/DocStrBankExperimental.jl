```julia
get_next_time(
    cache::InfrastructureSystems.TimeSeriesCache
) -> Any

```

Return the timestamp for the next read with [`get_next_time_series_array!`](@ref).

Return `nothing` if all data has been read.
