```
fmi2GetReal!(c::FMU2Component, vr::fmi2ValueReferenceFormat, values::AbstractArray{fmi2Real})
```

Get the values of an array of fmi2Real variables.

rites the real values of an array of variables in the given field

# Arguments

  * `c::fmi2Struct`:  Representative for an FMU in the FMI 2.0.2 Standard.

More detailed: `fmi2Struct = Union{FMU2, FMU2Component}`

  * `c::FMU2`: Mutable struct representing a FMU and all it instantiated instances in the FMI 2.0.2 Standard.
  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `vr::fmi2ValueReferenceFormat`: Wildcards for how a user can pass a fmi[X]ValueReference

More detailed: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

  * `values::AbstractArray{fm2Real}`: Argument `values` is an AbstractArray with the actual values of these variables.

# Returns

  * `status::fmi2Status`: Return `status` is an enumeration of type `fmi2Status` and indicates the success of the function call.

More detailed:

  * `fmi2OK`: all well
  * `fmi2Warning`: things are not quite right, but the computation can continue
  * `fmi2Discard`: if the slave computed successfully only a subinterval of the communication step
  * `fmi2Error`: the communication step could not be carried out at all
  * `fmi2Fatal`: if an error occurred which corrupted the FMU irreparably
  * `fmi2Pending`: this status is returned if the slave executes the function asynchronously

# Source

  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.24]: 2.1.7 Getting and Setting Variable Values
  * FMISpec2.0.2[p.18]: 2.1.3 Status Returned by Functions

See also [`fmi2GetReal!`](@ref).
