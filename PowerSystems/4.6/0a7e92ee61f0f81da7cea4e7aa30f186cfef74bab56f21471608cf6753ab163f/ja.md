```julia
get_flow_limits(
    value::PowerSystems.MonitoredLine
) -> NamedTuple{(:from_to, :to_from), <:Tuple{Any, Any}}

```

[`MonitoredLine`](@ref) の `flow_limits` を取得します。
