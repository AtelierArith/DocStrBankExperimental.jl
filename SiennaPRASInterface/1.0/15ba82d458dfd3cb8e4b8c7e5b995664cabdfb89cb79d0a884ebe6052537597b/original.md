```julia
generate_outage_profile!(
    sys::PowerSystems.System,
    method::PRASCore.Simulations.SequentialMonteCarlo
) -> PowerSystems.System

```

Analyze resource adequacy using Monte Carlo simulation and add the asset status from the worst sample to PSY.TimeSeriesForcedOutage of the component.

Uses default template with PSY.Area AggregationTopology.

# Arguments

  * `sys::PSY.System`: PowerSystems.jl system model
  * `method::PRASCore.SequentialMonteCarlo`: Simulation method to use

# Returns

```
- PSY System with PSY.TimeSeriesForcedOutage for all components for which asset status is available
```
