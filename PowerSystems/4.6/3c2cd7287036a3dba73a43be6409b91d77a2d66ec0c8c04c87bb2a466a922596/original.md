```julia
bulk_add_time_series!(
    sys::PowerSystems.System,
    associations;
    batch_size
) -> Vector{InfrastructureSystems.TimeSeriesKey}

```

Add time series in bulk.

Prefer use of [`begin_time_series_update`](@ref).

# Examples

```julia
# Assumes `read_time_series` will return data appropriate for Deterministic forecasts
# based on the generator name and the filenames match the component and time series names.
resolution = Dates.Hour(1)
associations = (
    IS.TimeSeriesAssociation(
        gen,
        Deterministic(
            data = read_time_series(get_name(gen) * ".csv"),
            name = "get_max_active_power",
            resolution=resolution),
    )
    for gen in get_components(ThermalStandard, sys)
)
bulk_add_time_series!(sys, associations)
```
