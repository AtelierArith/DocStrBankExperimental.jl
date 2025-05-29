```julia
execute!(
    sim::PowerSimulations.Simulation;
    kwargs...
) -> InfrastructureSystems.Simulation.RunStatusModule.RunStatus

```

Solves the simulation model for sequential Simulations.

# Arguments

  * `sim::Simulation=sim`: simulation object created by Simulation()

The optional keyword argument `exports` controls exporting of results to CSV files as the simulation runs.

# Example

```julia
sim = Simulation("Test", 7, problems, "/Users/folder")
execute!(sim::Simulation; kwargs...)
```
