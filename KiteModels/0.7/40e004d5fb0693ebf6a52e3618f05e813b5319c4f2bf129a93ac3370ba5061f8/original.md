```
reinit!(s::RamAirKite; prn=true, precompile=false) -> Nothing
```

Reinitialize an existing kite power system model with new state values.

This function performs the following operations:

1. If no integrator exists yet:

      * Loads a serialized ODEProblem from disk
      * Initializes a new ODE integrator
      * Generates getter/setter functions for the system
2. Converts measurement data to quaternion orientation
3. Initializes the point mass system with new positions
4. Sets initial values for all state variables
5. Reinitializes the ODE integrator
6. Updates the linearized aerodynamic model

This is more efficient than `init!` as it reuses the existing model structure and only updates the state variables to match the current `measure`.

# Arguments

  * `s::RamAirKite`: The kite power system state object
  * `prn::Bool=true`: Whether to print progress information

# Returns

  * `Nothing`

# Throws

  * `ArgumentError`: If no serialized problem exists (run `init_sim!` first)
