```julia
get_components_in_aggregation_topology(
    _::Type{T<:PowerSystems.StaticInjection},
    sys::PowerSystems.System,
    aggregator::PowerSystems.AggregationTopology
) -> Vector{T} where T<:PowerSystems.StaticInjection

```

AggregationTopology内のバスを持つコンポーネントのベクトルを返します。
