```
ReservoirLimitFeedforward(
    component_type::Type{<:PSY.Component},
    source::Type{T},
    affected_values::Vector{DataType},
    number_of_periods::Int,
    meta = CONTAINER_KEY_EMPTY_META
) where {T}
```

Adds a constraint to limit the sum of a variable over the number of periods to the source value.

# Arguments:

  * `component_type::Type{<:`[`PowerSystems.Component`](@extref)`}` : Specify the type of component on which the Feedforward will be applied
  * `source::Type{T}` : Specify the VariableType, ParameterType or AuxVariableType as the source of values for the Feedforward
  * `affected_values::Vector{DataType}` : Specify the variable on which the reservoir limit will be applied using the source values
  * `number_of_periods::Int` : Specify the total number of periods that are added on which the limits are applied. For example, in a 24-step simulation if `number_of_periods = 24`, it will add only one constraint over the sum of 24 periods on which the reservoir limit will be applied. If `number_of_periods = 12`, it will create two constraints, one for the first 12 steps and one for the 13:24 steps. It is mandatory that `number_of_periods` can divide the total number of simulation steps.
