```julia
is_component_in_aggregation_topology(
    comp::PowerSystems.Component,
    aggregator::PowerSystems.AggregationTopology
) -> Union{Missing, Bool}

```

Return whether the given component's bus is in the AggregationTopology.
