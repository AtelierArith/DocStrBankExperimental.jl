```julia
Deterministic(
    src::InfrastructureSystems.Deterministic,
    name::AbstractString;
    scaling_factor_multiplier
) -> InfrastructureSystems.Deterministic

```

Construct Deterministic that shares the data from an existing instance.

This is useful in cases where you want a component to use the same time series data for two different attributes.

# Examples

```julia
resolution = Dates.Hour(1)
data = Dict(
    DateTime("2020-01-01T00:00:00") => ones(24),
    DateTime("2020-01-01T01:00:00") => ones(24),
)
# Define a Deterministic for the first attribute
forecast_max_active_power = Deterministic(
    "max_active_power",
    data,
    resolution,
    scaling_factor_multiplier = get_max_active_power,
)
add_time_series!(sys, generator, forecast_max_active_power)
# Reuse time series for second attribute
forecast_max_reactive_power = Deterministic(
    forecast_max_active_power,
    "max_reactive_power"
    scaling_factor_multiplier = get_max_reactive_power,
)
add_time_series!(sys, generator, forecast_max_reactive_power)
```
