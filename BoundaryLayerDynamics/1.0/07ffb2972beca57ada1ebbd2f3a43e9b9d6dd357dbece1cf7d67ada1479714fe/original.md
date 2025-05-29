```
evolve!(model, tspan; dt, method, output)
```

Simulate a `model`’s evolution over time, optionally collecting data along the way.

# Arguments

  * `model::Model`: The [`Model`](@ref) containing the current state as well as the discretized processes that describe the rate of change of the state.
  * `tspan`: The time span over which the evolution of the model should be simulated. Can be a single `Number` with the total duration or a `Tuple` of `Number`s with the start and end times.

# Keywords

  * `dt`: The (constant) size of the time step (required). Note that `tspan` has to be divisible by `dt`.
  * `method = SSPRK33()`: The [time-integration method](@ref Time-Integration-Methods) used to solve the semi-discretized initial-value problem as an ordinary differential equation.
  * `output = []`: A list of [output modules](@ref Output-Modules) that collect data during the simulation.
