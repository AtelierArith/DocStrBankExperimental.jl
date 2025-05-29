```julia
assess(
    sys::PowerSystems.System,
    method::PRASCore.Simulations.SequentialMonteCarlo,
    resultsspecs::PRASCore.Results.ResultSpec...
) -> Any

```

Analyze resource adequacy using Monte Carlo simulation.

Uses default template with Area level aggregation.

# Arguments

  * `sys::PSY.System`: PowerSystems.jl system model
  * `method::PRASCore.SequentialMonteCarlo`: Simulation method to use
  * `resultsspec::PRASCore.Results.ResultSpec...`: Results to compute

# Returns

  * Tuple of results from `resultsspec`: default is ([`ShortfallResult`](@ref),)
