```julia
assess(
    sys::PowerSystems.System,
    template::SiennaPRASInterface.RATemplate,
    method::PRASCore.Simulations.SequentialMonteCarlo,
    resultsspecs::PRASCore.Results.ResultSpec...
) -> Any

```

Analyze resource adequacy using Monte Carlo simulation.

# Arguments

  * `sys::PSY.System`: PowerSystems.jl system model
  * `template::RATemplate`: PRAS problem template
  * `method::PRASCore.SequentialMonteCarlo`: Simulation method to use
  * `resultsspec::PRASCore.Results.ResultSpec...`: Results to compute

# Returns

  * Tuple of results from `resultsspec`: default is ([`ShortfallResult`](@ref),)
