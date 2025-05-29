```
SemiContinuousFeedforward(
    component_type::Type{<:PSY.Component},
    source::Type{T},
    affected_values::Vector{DataType},
    meta = CONTAINER_KEY_EMPTY_META
) where {T}
```

It allows to enable/disable bounds to 0.0 for a specified variable. Commonly used to limit the `ActivePowerVariable` in an Economic Dispatch problem by the commitment decision taken in an another problem (typically a Unit Commitment problem).

# Arguments:

  * `component_type::Type{<:PSY.Component}` : Specify the type of component on which the Feedforward will be applied
  * `source::Type{T}` : Specify the VariableType, ParameterType or AuxVariableType as the source of values for the Feedforward
  * `affected_values::Vector{DataType}` : Specify the variable on which the semicontinuous limit will be applied using the source values
