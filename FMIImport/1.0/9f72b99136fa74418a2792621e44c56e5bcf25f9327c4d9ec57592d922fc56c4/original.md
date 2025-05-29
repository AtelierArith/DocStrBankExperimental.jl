```
fmi3SerializeFMUState(c::FMU3Instance, state::fmi3FMUState)
```

Serializes the data referenced by the pointer FMUstate and copies this data into the byte vector serializedState of length size to be provided by the environment.

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.
  * `state::fmi3FMUState`: Argument `state` is a pointer to a data structure in the FMU that saves the internal FMU state of the actual or a previous time instant.

# Returns

  * `serializedState:: Array{fmi3Byte}`: Return `serializedState` contains the copy of the serialized data referenced by the pointer FMUstate

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 Platform Dependent Definitions
  * FMISpec3.0: 2.2.6.4. Getting and Setting the Complete FMU State

See also [`fmi3SerializeFMUState`](@ref).
