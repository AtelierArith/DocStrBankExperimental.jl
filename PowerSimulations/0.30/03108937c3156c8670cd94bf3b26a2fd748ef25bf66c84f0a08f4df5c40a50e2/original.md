```julia
SimulationResults(
    path::AbstractString,
    name::AbstractString;
    ...
) -> PowerSimulations.SimulationResults
SimulationResults(
    path::AbstractString,
    name::AbstractString,
    execution;
    ignore_status
) -> PowerSimulations.SimulationResults

```

Construct SimulationResults from a simulation output directory.

# Arguments

  * `path::AbstractString`: Simulation output directory
  * `name::AbstractString`: Simulation name
  * `execution::AbstractString`: Execution number. Default is the most recent.
  * `ignore_status::Bool`: If true, return results even if the simulation failed.
