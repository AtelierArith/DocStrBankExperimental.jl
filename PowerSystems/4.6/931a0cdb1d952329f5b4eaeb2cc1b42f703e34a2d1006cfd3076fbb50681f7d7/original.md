```julia
get_aggregation_topology_accessor(
    _::Type{T<:PowerSystems.AggregationTopology}
) -> typeof(PowerSystems.get_load_zone)

```

Return the method to be called on a ACBus to get its AggregationTopology value for this type.
