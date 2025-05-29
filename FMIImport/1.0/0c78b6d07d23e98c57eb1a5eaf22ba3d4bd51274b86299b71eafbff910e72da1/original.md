fmi2GetReal(c::FMU2Component, vr::fmi2ValueReferenceFormat)

Get the values of an array of fmi2Real variables.

# Arguments

  * `c::fmi2Struct`:  Representative for an FMU in the FMI 2.0.2 Standard.

More detailed: `fmi2Struct = Union{FMU2, FMU2Component}`

  * `c::FMU2`: Mutable struct representing a FMU and all it instantiated instances in the FMI 2.0.2 Standard.
  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `vr::fmi2ValueReferenceFormat`: wildcards for how a user can pass a fmi[X]ValueReference

More detailed: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

# Returns

  * `values::Array{fm2Real}`: Returns values of an array of fmi2Real variables with the dimension of fmi2ValueReferenceFormat length.

# Source

  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.24]: 2.1.7 Getting and Setting Variable Values
  * FMISpec2.0.2[p.18]: 2.1.3 Status Returned by Functions

See also [`fmi2GetReal`](@ref).
