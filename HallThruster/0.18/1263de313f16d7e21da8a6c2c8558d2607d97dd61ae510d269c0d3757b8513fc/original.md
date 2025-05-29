```julia
run_simulation(config::HallThruster.Config; kwargs...)

```

**Deprecated**. Please use `run_simulation(::Config, ::SimParams; kwargs...)`

Run a Hall thruster simulation using the provided Config object.

## Arguments

  * `config`: a `Config` containing simulation parameters.
  * `dt`: The timestep, in seconds. Typical values are O(10 ns) (1e-8 seconds).
  * `duration`: How long to run the simulation, in seconds (simulation time, not wall time). Typical runtimes are O(1 ms) (1e-3 seconds).
  * `ncells`: How many cells to use. Typical values are 100 - 1000 cells.
  * `nsave`: How many frames to save.
