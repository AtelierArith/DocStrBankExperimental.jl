```
fmi2GetReal!(c::FMU2Component, vr::AbstractArray{fmi2ValueReference}, nvr::Csize_t, value::AbstractArray{fmi2Real})
```

Functions to get and set values of variables idetified by their valueReference

# Arguments

  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `vr::AbstractArray{fmi2ValueReference}`: Argument `vr` is an AbstractArray of `nvr` value handels called "ValueReference" that define the variable that shall be inquired.
  * `nvr::Csize_t`: Argument `nvr` defines the size of `vr`.
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
  * FMISpec2.0.2[p.18]: 2.1.3 Status Returned by Functions
  * FMISpec2.0.2[p.24]: 2.1.7 Getting and Setting Variable Values

See also [`fmi2GetReal!`](@ref).
