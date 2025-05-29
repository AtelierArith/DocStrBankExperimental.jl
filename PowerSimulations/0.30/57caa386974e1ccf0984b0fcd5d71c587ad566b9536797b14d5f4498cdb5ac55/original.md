```julia
build!(
    sim::PowerSimulations.Simulation;
    recorders,
    console_level,
    file_level,
    serialize,
    partitions,
    index
) -> InfrastructureSystems.Simulation.SimulationBuildStatusModule.SimulationBuildStatus

```

Build the Simulation, problems and the related folder structure.

# Arguments

  * `sim::Simulation`: simulation object
  * `recorders::Vector{Symbol} = []`: recorder names to register
  * `serialize::Bool = true`: serializes the simulation objects in the simulation
  * `console_level = Logging.Error`:
  * `file_level = Logging.Info`:
