```
(model::HydroModel)(input::AbstractArray, params::ComponentVector; kwargs...)
```

Runs the hydrological model simulation using the provided input data and parameters.

# Arguments

  * `input::AbstractArray{T,D}`: Input data. Shape can be `(variables, timesteps)` (D=2, single-node) or `(variables, nodes, timesteps)` (D=3, multi-node).
  * `params::ComponentVector`: Model parameters, structured according to the components' requirements.

# Keyword Arguments

  * `initstates::ComponentVector`: Optional initial states for stateful components. Defaults to component-defined defaults.
  * `config::Union{NamedTuple, Vector{<:NamedTuple}}`: Optional configuration for components (e.g., ODE solver, interpolation). Can be a single `NamedTuple` applied to all, or a `Vector` for component-specific settings.
  * `kwargs...`: Other keyword arguments passed down to individual components if applicable.

# Returns

  * `AbstractArray`: Model output, with shape matching the input's time (and node, if D=3) dimensions: `(output_variables, timesteps)` or `(output_variables, nodes, timesteps)`.

# Example

```julia
# Assuming 'model' is a constructed HydroModel instance
# input_data might be Matrix or 3D Array
# parameters is a ComponentVector
output = model(input_data, parameters; initstates=initial_conditions)
```

# Notes

  * The function orchestrates data flow through the model's components sequentially.
  * Input variable dimension (`size(input, 1)`) must match `get_input_names(model)`.
  * State evolution and output collection are handled internally.
