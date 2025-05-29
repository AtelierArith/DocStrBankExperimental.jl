```
fmi2SerializeFMUstate!(c::FMU2Component, FMUstate::fmi2FMUstate, serialzedState::AbstractArray{fmi2Byte}, size::Csize_t)
```

Serializes the data which is referenced by pointer `FMUstate` and copies this data in to the byte vector `serializedState` of length `size`, that must be provided by the environment.

# Arguments

  * `str::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `state::fmi2FMUstate`: Argument `state` is a pointer to a data structure in the FMU that saves the internal FMU state of the actual or a previous time instant.
  * `serialzedState::AbstractArray{fmi2Byte}`: Argument `serializedState` contains the copy of the serialized data referenced by the pointer FMUstate.
  * `size::Csize_t`: Argument `size` defines the length of the serialized vector.

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
  * FMISpec2.0.2[p.16]: 2.1.2 Platform Dependent Definitions (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 Status Returned by Functions
  * FMISpec2.0.2[p.25]: 2.1.8 Getting and Setting the Complete FMU State

See also [`fmi2SerializeFMUstate`](@ref).
