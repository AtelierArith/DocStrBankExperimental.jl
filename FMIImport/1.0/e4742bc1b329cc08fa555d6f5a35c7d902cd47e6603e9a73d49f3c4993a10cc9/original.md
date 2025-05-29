```
fmi2GetString!(c::FMU2Component, vr::AbstractArray{fmi2ValueReference}, nvr::Csize_t, value::Union{AbstractArray{Ptr{Cchar}}, AbstractArray{Ptr{UInt8}}})
```

Functions to get and set values of variables idetified by their valueReference

These functions are especially used to get the actual values of output variables if a model is connected with other models.

# Arguments

  * `str::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `vr::AbstractArray{fmi2ValueReference}`: Argument `vr` is an array of `nvr` value handels called "ValueReference" that define the variable that shall be inquired.
  * `nvr::Csize_t`: Argument `nvr` defines the size of `vr`.
  * `value::Union{AbstractArray{Ptr{Cchar}, AbstractArray{Ptr{UInt8}}}`: The `value` argument is an AbstractArray of values whose memory address refers to data of type Cchar or UInt8and describes a vector with the actual values of these. variables.

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

See also [`fmi2GetString!`](@ref).
