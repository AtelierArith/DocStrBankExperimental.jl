```
fmi2DeSerializeFMUstate!(c::FMU2Component, serializedState::AbstractArray{fmi2Byte}, size::Csize_t, FMUstate::Ref{fmi2FMUstate})
```

Deserializes the byte vector serializedState of length size, constructs a copy of the FMU state and stores the FMU state in the given address of the reference `FMUstate`, the pointer to this copy.

# Arguments

  * `str::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `state::fmi2FMUstate`: Argument `state` is a pointer to a data structure in the FMU that saves the internal FMU state of the actual or a previous time instant.
  * `serialzedState::AbstractArray{fmi2Byte}`: Argument `serializedState` contains the copy of the serialized data referenced by the pointer FMUstate.
  * `size::Csize_t`: Argument `size` defines the length of the serialized vector.
  * `FMUstate::Ref{fmi2FMUstate}`: Argument `FMUstate` is an object that safely references data of type `fmi3FMUstate` which is a pointer to a data structure in the FMU that saves the internal FMU state of the actual or a previous time instant.

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

See also [`fmi2DeSerializeFMUstate!`](@ref).
