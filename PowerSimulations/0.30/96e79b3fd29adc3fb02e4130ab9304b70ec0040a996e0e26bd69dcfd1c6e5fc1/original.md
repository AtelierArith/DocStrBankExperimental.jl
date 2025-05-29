```julia
solve!(
    step::Int64,
    model::PowerSimulations.EmulationModel,
    start_time::Dates.DateTime,
    store::PowerSimulations.SimulationStore;
    exports
) -> InfrastructureSystems.Simulation.RunStatusModule.RunStatus

```

Default solve method for an EmulationModel used inside of a Simulation. Solves problems that conform to the requirements of DecisionModel{<: DecisionProblem}

# Arguments

  * `step::Int`: Simulation Step
  * `model::OperationModel`: operation model
  * `start_time::Dates.DateTime`: Initial Time of the simulation step in Simulation time.
  * `store::SimulationStore`: Simulation output store
  * `exports = nothing`: realtime export of output. Use wisely, it can have negative impacts in the simulation times
