```julia
get_active_power_limits(
    value::PowerSystems.InterconnectingConverter
) -> NamedTuple{(:min, :max), <:Tuple{Any, Any}}

```

[`InterconnectingConverter`](@ref) の `active_power_limits` を取得します。
