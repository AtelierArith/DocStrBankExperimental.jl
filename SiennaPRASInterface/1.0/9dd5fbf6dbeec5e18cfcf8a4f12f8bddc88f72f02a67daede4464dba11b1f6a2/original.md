```
generate_outage_profile!(
    sys::PSY.System,
    aggregation::Type{AT},
    method::PRASCore.SequentialMonteCarlo,
) where {AT <: PSY.AggregationTopology, RM <: PRASCore.Results.ReliabilityMetric}
```

Analyze resource adequacy using Monte Carlo simulation and add the asset status from the worst sample to PSY.TimeSeriesForcedOutage of the component.

# Arguments

  * `sys::PSY.System`: PowerSystems.jl system model
  * `aggregation::Type{AT}`: Aggregation topology to use in translating to PRAS
  * `method::PRASCore.SequentialMonteCarlo`: Simulation method to use

# Returns

  * PSY System with PSY.TimeSeriesForcedOutage for all components for which asset status is available
