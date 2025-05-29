```
fmi2GetBoolean(c::FMU2Component, vr::fmi2ValueReferenceFormat)
```

Get the values of an array of fmi2Boolean variables.

# Arguments

  * `c::fmi2Struct`:  Representative for an FMU in the FMI 2.0.2 Standard.

More detailed: `fmi2Struct = Union{FMU2, FMU2Component}`

  * `c::FMU2`: Mutable struct representing a FMU and all it instantiated instances in the FMI 2.0.2 Standard.
  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `vr::fmi2ValueReferenceFormat`: Argument `vr` defines the value references of the variables.

More detailed: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

# Returns

  * `values::Array{fmi2Boolean}`: Return `values` is an array with the actual values of these variables.

See also [`fmi2GetBoolean!`](@ref).
