```julia
get_buses(
    sys::PowerSystems.System,
    aggregator::PowerSystems.AggregationTopology
) -> Vector{PowerSystems.ACBus}

```

AggregationTopologyに含まれるバスのベクターを返します。
