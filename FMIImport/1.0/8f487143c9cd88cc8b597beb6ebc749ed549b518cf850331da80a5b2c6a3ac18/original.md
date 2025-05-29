fmi3SerializeFMUState(c::FMU3Instance, state::fmi3FMUState)

Serializes the data referenced by the pointer FMUstate and copies this data into the byte vector serializedState of length size to be provided by the environment.

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.
  * `serializedState::Array{fmi3Byte}`: Argument `serializedState` contains the fmi3Byte field to be deserialized.

# Returns

  * Return `state` is a pointer to a copy of the internal FMU state.

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 Platform Dependent Definitions
  * FMISpec3.0: 2.2.6.4. Getting and Setting the Complete FMU State

See also [`fmi3DeSerializeFMUState`](@ref).
