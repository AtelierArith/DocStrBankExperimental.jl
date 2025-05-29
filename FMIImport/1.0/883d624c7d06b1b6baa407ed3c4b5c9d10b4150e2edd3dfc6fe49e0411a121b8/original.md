```
fmi3DeSerializeFMUState!(c::FMU3Instance, serialzedState::AbstractArray{fmi3Byte}, size::Csize_t, FMUstate::Ref{fmi3FMUState})
```

Deserializes the byte vector serializedState of length size, constructs a copy of the FMU state and stores the FMU state in the given address of the reference `FMUstate`, the pointer to this copy.

# Arguments

  * `c::FMU3Instance`: Argument `c` is a Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.
  * `FMUstate::fmi3FMUstate`: Argument `FMUstate` is a pointer to a data structure in the FMU that saves the internal FMU state of the actual or a previous time instant.
  * `serialzedState::AbstractArray{fmi3Byte}`: Argument `serializedState` contains the copy of the serialized data referenced by the pointer FMUstate.
  * `size::Ref{Csize_t}`: Argument `size` is an object that safely references a value of type `Csize_t` and defines the size of the byte vector in which the FMUstate can be stored.

# Returns

  * `status::fmi3Status`: Return `status` is an enumeration of type `fmi3Status` and indicates the success of the function call.

More detailed:

  * `fmi3OK`: all well
  * `fmi3Warning`: things are not quite right, but the computation can continue
  * `fmi3Discard`: if the slave computed successfully only a subinterval of the communication step
  * `fmi3Error`: the communication step could not be carried out at all
  * `fmi3Fatal`: if an error occurred which corrupted the FMU irreparably

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 Platform Dependent Definitions
  * FMISpec3.0: 2.2.4 Status Returned by Functions
  * FMISpec3.0: 2.2.6.4. Getting and Setting the Complete FMU State

See also [`fmi3DeSerializeFMUState!`](@ref).
