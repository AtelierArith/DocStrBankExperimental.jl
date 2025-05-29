```
fmi2GetRealOutputDerivatives(c::FMU2Component, vr::fmi2ValueReferenceFormat, order::AbstractArray{fmi2Integer})
```

Sets the n-th time derivative of real input variables.

# Arguments

  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `vr::Array{fmi2ValueReference}`: Argument `vr` is an array of `nvr` value handels called "ValueReference" that t define the variables whose derivatives shall be set.
  * `order::Array{fmi2Integer}`: Argument `order` is an array of fmi2Integer values witch specifys the corresponding order of derivative of the real input variable.

# Returns

  * `value::AbstactArray{fmi2Integer}`: Return `value` is an array which represents a vector with the values of the derivatives.

# Source

  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 Platform Dependent Definitions
  * FMISpec2.0.2[p.18]: 2.1.3 Status Returned by Functions
  * FMISpec2.0.2[p.104]: 4.2.1 Transfer of Input / Output Values and Parameters
