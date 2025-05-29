```julia
get_active_power_flow_limits(
    value::PowerSystems.TransmissionInterface
) -> NamedTuple{(:min, :max), <:Tuple{Any, Any}}

```

Get [`TransmissionInterface`](@ref) `active_power_flow_limits`.
