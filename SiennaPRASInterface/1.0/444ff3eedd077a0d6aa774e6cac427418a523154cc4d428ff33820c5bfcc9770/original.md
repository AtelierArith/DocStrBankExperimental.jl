```
assess(
    sys::PSY.System,
    aggregation::Type{AT},
    method::PRASCore.SequentialMonteCarlo,
    resultsspecs::PRASCore.Results.ResultSpec...,
) where {AT <: PSY.AggregationTopology}
```

Analyze resource adequacy using Monte Carlo simulation.

# Arguments

  * `sys::PSY.System`: PowerSystems.jl system model
  * `aggregation::Type{AT}`: Aggregation topology to use in translating to PRAS
  * `method::PRASCore.SequentialMonteCarlo`: Simulation method to use
  * `resultsspec::PRASCore.Results.ResultSpec...`: Results to compute

# Returns

  * Tuple of results from `resultsspec`: default is ([`ShortfallResult`](@ref),)
