```
ReservoirTargetFeedforward(
    component_type::Type{<:PowerSystems.Component},
    source::Type{T},
    affected_values::Vector{DataType},
    target_period::Int,
    penalty_cost::Float64,
    meta = CONTAINER_KEY_EMPTY_META
) where {T}
```

Adds a constraint to enforce a minimum reservoir level target with a slack variable associated with a penalty term.

# Arguments:

  * `component_type::Type{<:`[`PowerSystems.Component`](@extref)`}` : Specify the type of component on which the Feedforward will be applied
  * `source::Type{T}` : Specify the VariableType, ParameterType or AuxVariableType as the source of values for the Feedforward
  * `affected_values::Vector{DataType}` : Specify the variable on which the reservoir target will be applied using the source values
  * `target_period::Int` : Specify the time step at which the reservoir target will be applied.
  * `penalty_cost::Float64` : Specify the penalty cost for not reaching the desired reservoir target.
