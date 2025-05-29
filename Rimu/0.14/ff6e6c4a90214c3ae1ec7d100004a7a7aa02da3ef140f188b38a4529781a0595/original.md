```
solve!(sm::PMCSimulation; kwargs...)::PMCSimulation
```

Solve a [`Rimu.PMCSimulation`](@ref) until the last step is completed or the wall time limit is reached.

To continue a previously completed simulation, set a new `last_step` or `wall_time` using the keyword arguments. Optionally, changes can be made to the `replica_strategy`, the `post_step_strategy`, or the `reporting_strategy`.

# Optional keyword arguments:

  * `last_step = nothing`: Set the last step to a new value and continue the simulation.
  * `wall_time = nothing`: Set the allowed wall time to a new value and continue the   simulation.
  * `reset_time = false`: Reset the `elapsed_time` counter and continue the simulation.
  * `empty_report = false`: Empty the report before continuing the simulation.
  * `replica_strategy = nothing`: Change the replica strategy. Requires the number of replicas   to match the number of replicas in the simulation `sm`. Implies `empty_report = true`.
  * `post_step_strategy = nothing`: Change the post-step strategy. Implies   `empty_report = true`.
  * `reporting_strategy = nothing`: Change the reporting strategy. Implies   `empty_report = true`.
  * `metadata = nothing`: Add metadata to the report.

See also [`ProjectorMonteCarloProblem`](@ref), [`init`](@ref), [`solve`](@ref), [`step!`](@ref), [`Rimu.PMCSimulation`](@ref).
