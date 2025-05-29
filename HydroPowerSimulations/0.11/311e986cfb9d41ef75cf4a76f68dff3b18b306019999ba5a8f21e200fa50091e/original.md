```
HydroUsageLimitFeedforward(
    component_type::Type{<:PowerSystems.Component},
    source::Type{T},
    affected_values::Vector{DataType},
    meta = CONTAINER_KEY_EMPTY_META
) where {T}
```

Adds a constraint to enforce a maximum usage of hydro energy based on the source value. It is recommended to use the Auxiliary Variable HydroEnergyOutput as Source, affecting the HydroUsageLimitParameter.

# Arguments:

  * `component_type::Type{<:`[`PowerSystems.Component`](@extref)`}` : Specify the type of component on which the Feedforward will be applied
  * `source::Type{T}` : Specify the VariableType, ParameterType or AuxVariableType as the source of values for the Feedforward
  * `affected_values::Vector{DataType}` : Specify the variable on which the hydro limit will be applied using the source values
