```
FixValueFeedforward(
    component_type::Type{<:PSY.Component},
    source::Type{T},
    affected_values::Vector{DataType},
    meta = CONTAINER_KEY_EMPTY_META
) where {T}
```

Fixes a Variable or Parameter Value in the model from another problem. Is the only Feed Forward that can be used with a Parameter or a Variable as the affected value.

# Arguments:

  * `component_type::Type{<:PSY.Component}` : Specify the type of component on which the Feedforward will be applied
  * `source::Type{T}` : Specify the VariableType, ParameterType or AuxVariableType as the source of values for the Feedforward
  * `affected_values::Vector{DataType}` : Specify the variable on which the fix value will be applied using the source values
