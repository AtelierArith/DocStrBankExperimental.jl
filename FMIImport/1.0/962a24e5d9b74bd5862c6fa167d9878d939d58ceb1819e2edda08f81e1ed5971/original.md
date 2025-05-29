```
fmi2GetString!(c::FMU2Component, vr::fmi2ValueReferenceFormat, values::AbstractArray{fmi2String})
```

Writes the string values of an array of variables in the given field

These functions are especially used to get the actual values of output variables if a model is connected with other models.

# Arguments

  * `str::fmi2Struct`:  Representative for an FMU in the FMI 2.0.2 Standard.

More detailed: `fmi2Struct = Union{FMU2, FMU2Component}`

  * `str::FMU2`: Mutable struct representing a FMU and all it instantiated instances in the FMI 2.0.2 Standard.
  * `str::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `vr::fmi2ValueReferenceFormat`: Argument `vr` defines the value references of the variables.

More detailed: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

  * `values::AbstractArray{fmi2String}`: Argument `values` is an AbstractArray with the actual values of these variables

# Returns

  * Return singleton instance of type `Nothing`, if there is no value to return (as in a C void function) or when a variable or field holds no value.

# Source

  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.24]: 2.1.7 Getting and Setting Variable Values
  * FMISpec2.0.2[p.16]: 2.1.2 Platform Dependent Definitions
  * FMISpec2.0.2[p.18]: 2.1.3 Status Returned by Functions

See also [`fmi2GetString!`](@ref).
