```julia
get_buses(
    sys::PowerSystems.System,
    aggregator::PowerSystems.AggregationTopology
) -> Vector{PowerSystems.ACBus}

```

Return a vector of buses contained within the AggregationTopology.
