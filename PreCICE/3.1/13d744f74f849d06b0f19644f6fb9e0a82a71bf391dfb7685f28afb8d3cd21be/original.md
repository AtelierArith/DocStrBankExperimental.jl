```
advance(computedTimestepLength::Float64)
```

Advances preCICE after the solver has computed one time step.

This function does the following:

  * Sends and resets coupling data written by solver to coupling partners.
  * Receives coupling data read by solver.
  * Computes and applies data mappings.
  * Computes acceleration of coupling data.
  * Exchanges and computes information regarding the state of the coupled simulation.

# Arguments

  * `computed_timestep_length::Float64`: Size of time step used by the solver.

# Notes

Previous calls:

  * [`initialize`](@ref) has been called successfully.
  * The solver has computed one timestep.
  * The solver has written all coupling data.
  * [`finalize`](@ref) has not yet been called.
