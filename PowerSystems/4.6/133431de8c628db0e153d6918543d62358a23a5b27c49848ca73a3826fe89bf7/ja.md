```julia
make_selector(
    component_type::Type{<:PowerSystems.Component},
    topology_type::Type{<:PowerSystems.AggregationTopology},
    topology_name::AbstractString;
    groupby,
    name
) -> PowerSystems.TopologyComponentSelector

```

`AggregationTopology` とコンポーネントの型から `ComponentSelector` を作成します。オプションで、`ComponentSelector` の名前やグルーピング動作を提供できます。
