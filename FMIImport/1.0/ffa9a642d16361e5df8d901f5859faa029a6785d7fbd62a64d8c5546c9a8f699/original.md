```
fmi2SetString(c::FMU2Component, vr::fmi2ValueReferenceFormat, values::Union{AbstractArray{String}, String})
```

Set the values of an array of string variables

For the exact rules on which type of variables fmi2SetXXX can be called see FMISpec2.0.2 section 2.2.7 , as well as FMISpec2.0.2 section 3.2.3 in case of ModelExchange and FMISpec2.0.2 section 4.2.4 in case of CoSimulation.

# Arguments

  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `vr::fmi2ValueReferenceFormat`: Argument `vr` defines the value references of the variables.

More detailed: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

  * `values::Union{Array{String}, String}`: Argument `values` is an array or a single value with type String.

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
  * FMISpec2.0.2[p.16]: 2.1.2 Platform Dependent Definitions
  * FMISpec2.0.2[p.18]: 2.1.3 Status Returned by Functions
  * FMISpec2.0.2[p.24]: 2.1.7 Getting and Setting Variable Values
  * FMISpec2.0.2[p.46]: 2.2.7 Definition of Model Variables
  * FMISpec2.0.2[p.46]: 3.2.3 State Machine of Calling Sequence
  * FMISpec2.0.2[p.108]: 4.2.4 State Machine of Calling Sequence from Master to Slave

See also [`fmi2SetString`](@ref).
