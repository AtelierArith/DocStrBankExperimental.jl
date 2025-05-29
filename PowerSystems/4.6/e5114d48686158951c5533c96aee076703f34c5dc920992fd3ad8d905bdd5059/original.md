```julia
get_aggregation_topology_mapping(
    _::Type{T<:PowerSystems.AggregationTopology},
    sys::PowerSystems.System
) -> Dict{String, Vector{PowerSystems.ACBus}}

```

Return a mapping of AggregationTopology name to vector of buses within it.
