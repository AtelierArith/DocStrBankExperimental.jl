```
fmi2GetInteger!(c::FMU2Component, vr::AbstractArray{fmi2ValueReference}, nvr::Csize_t, value::AbstractArray{fmi2Integer})
```

Writes the integer values of an array of variables in the given field

fmi2GetInteger! is only possible for arrays of values, please use an array instead of a scalar.

# Arguments

  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `vr::AbstractArray{fmi2ValueReference}`: Argument `vr` is an AbstractArray of `nvr` value handels, called "ValueReference" that define the variable that shall be inquired.
  * `nvr::Csize_t`: Argument `nvr` defines the size of `vr`.
  * `values::AbstractArray{fmi2Integer}`: Argument `values` is an AbstractArray with the actual values of these variables.

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

See also [`fmi2GetInteger!`](@ref).
