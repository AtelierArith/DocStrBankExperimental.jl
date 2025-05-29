```
LowerBoundFeedforward(
    component_type::Type{<:PSY.Component},
    source::Type{T},
    affected_values::Vector{DataType},
    add_slacks::Bool = false,
    meta = CONTAINER_KEY_EMPTY_META
) where {T}
```

Constructs a parameterized lower bound constraint to implement feedforward from other models.

# Arguments:

  * `component_type::Type{<:PSY.Component}` : Specify the type of component on which the Feedforward will be applied
  * `source::Type{T}` : Specify the VariableType, ParameterType or AuxVariableType as the source of values for the Feedforward
  * `affected_values::Vector{DataType}` : Specify the variable on which the lower bound will be applied using the source values
  * `add_slacks::Bool = false` : Add slacks variables to relax the lower bound constraint.
