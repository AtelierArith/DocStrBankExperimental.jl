```
simulate(state0, model, timesteps, parameters = setup_parameters(model))
simulate(state0, model, timesteps, info_level = 3)
simulate(state0, model, timesteps; <keyword arguments>)
```

Simulate a set of `timesteps` with `model` for the given initial `state0` and optionally specific parameters. Additional keyword arguments are passed onto [`simulator_config`](@ref) and [`simulate!`](@ref). This interface is primarily for convenience, as all storage for the simulator is allocated upon use and discared upon return. If you want to perform multiple simulations with the same model it is advised to instead instantiate [`Simulator`](@ref)  and combine it with [`simulate!`](@ref).

# Arguments

  * `state0::Dict`: initial state, typically created using [`setup_state`](@ref) for the `model` in use.
  * `model::JutulModel`: model that describes the discretized system to solve, for example [`SimulationModel`](@ref) or [`MultiModel`](@ref).
  * `timesteps::AbstractVector`: Vector of desired report steps. The simulator will perform time integration until `sum(timesteps)`  is reached, providing outputs at the end of each report step.
  * `parameters=setup_parameters(model)`: Optional overrides the default parameters for the model.
  * `forces=nothing`: Either `nothing` (for no forces), a single set of forces from `setup_forces(model)` or a `Vector` of such forces with equal length to `timesteps`.
  * `restart=nothing`: If an integer is provided, the simulation will attempt to restart from that step. Requires that `output_path` is provided here or in the `config`.
  * `config=simulator_config(model)`: Configuration `Dict` that holds many fine grained settings for output, linear solver, time-steps, outputs etc.

Additional arguments are passed onto [`simulator_config`](@ref).

See also [`simulate!`](@ref), [`Simulator`](@ref), [`SimulationModel`](@ref), [`simulator_config`](@ref).
