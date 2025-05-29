```julia
SingleTimeSeries(
    name::String,
    resolution::Dates.Period,
    initial_time::Dates.DateTime,
    time_steps::Int64
) -> InfrastructureSystems.SingleTimeSeries

```

Construct SingleTimeSeries after constructing a TimeArray from `initial_time` and `time_steps`.
