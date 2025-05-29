```julia
generate_outage_profile!(
    sys::PowerSystems.System,
    template::SiennaPRASInterface.RATemplate,
    method::PRASCore.Simulations.SequentialMonteCarlo
) -> PowerSystems.System

```

Analyze resource adequacy using Monte Carlo simulation and add the asset status from the worst sample to PSY.TimeSeriesForcedOutage of the component.

# Arguments

  * `sys::PSY.System`: PowerSystems.jl system model
  * `template::RATemplate`: PRAS problem template
  * `method::PRASCore.SequentialMonteCarlo`: Simulation method to use

# Returns

  * PSY System with PSY.TimeSeriesForcedOutage for all components for which asset status is available
