```julia
get_aggregation_topology_mapping(
    _::Type{T<:PowerSystems.AggregationTopology},
    sys::PowerSystems.System
) -> Dict{String, Vector{PowerSystems.ACBus}}

```

AggregationTopologyの名前とその中のバスのベクターのマッピングを返します。
