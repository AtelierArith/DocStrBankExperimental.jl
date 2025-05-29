```julia
get_system!(
    results::Union{InfrastructureSystems.Optimization.OptimizationProblemResults, PowerSimulations.SimulationProblemResults};
    kwargs...
) -> Union{Nothing, InfrastructureSystems.InfrastructureSystemsType}

```

Return the system used for the problem. If the system hasn't already been deserialized or set with [`set_system!`](@ref) then deserialize and store it.

If the simulation was configured to serialize all systems to file then the returned system will include all data. If that was not configured then the returned system will include all data except time series data.
