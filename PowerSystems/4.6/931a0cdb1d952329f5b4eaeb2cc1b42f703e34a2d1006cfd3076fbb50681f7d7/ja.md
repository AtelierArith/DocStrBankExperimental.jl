```julia
get_aggregation_topology_accessor(
    _::Type{T<:PowerSystems.AggregationTopology}
) -> typeof(PowerSystems.get_load_zone)

```

この型のAggregationTopology値を取得するためにACBusで呼び出すべきメソッドを返します。
