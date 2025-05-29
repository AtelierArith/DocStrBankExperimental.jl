```julia
SingleTimeSeries(
    name::String,
    resolution::Dates.Period,
    initial_time::Dates.DateTime,
    time_steps::Int64
) -> InfrastructureSystems.SingleTimeSeries

```

`initial_time` と `time_steps` から TimeArray を構築した後に SingleTimeSeries を構築します。
