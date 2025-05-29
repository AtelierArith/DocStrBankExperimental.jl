```julia
is_component_in_aggregation_topology(
    comp::PowerSystems.Component,
    aggregator::PowerSystems.AggregationTopology
) -> Union{Missing, Bool}

```

与えられたコンポーネントのバスがAggregationTopologyに含まれているかどうかを返します。
