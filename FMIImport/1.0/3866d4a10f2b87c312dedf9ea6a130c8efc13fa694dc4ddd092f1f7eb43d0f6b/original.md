```
fmi2SetBoolean(c::FMU2Component, vr::fmi2ValueReferenceFormat, values::Union{AbstractArray{Bool}, Bool})
```

Set the values of an array of boolean variables

# Arguments

  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `vr::fmi2ValueReferenceFormat`: Argument `vr` defines the value references of the variables.

More detailed: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

  * `values::Union{Array{Bool}, Bool}`: Argument `values` is an array or a single value with type Boolean or any subtyp

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
  * FMISpec2.0.2[p.16]: 2.1.2 Platform Dependent Definitions
  * FMISpec2.0.2[p.18]: 2.1.3 Status Returned by Functions

See also [`fmi2GetBoolean!`](@ref).
