```julia
make_selector(
    component_type::Type{<:PowerSystems.Component},
    topology_type::Type{<:PowerSystems.AggregationTopology},
    topology_name::AbstractString;
    groupby,
    name
) -> PowerSystems.TopologyComponentSelector

```

Make a `ComponentSelector` from an `AggregationTopology` and a type of component. Optionally provide a name and/or grouping behavior for the `ComponentSelector`.
