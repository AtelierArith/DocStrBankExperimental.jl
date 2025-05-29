```
fmi2SerializeFMUstate(c::FMU2Component, state::fmi2FMUstate)
```

Serializes the data referenced by the pointer FMUstate and copies this data into the byte vector serializedState of length size to be provided by the environment.

# Arguments

  * `str::fmi2Struct`:  Representative for an FMU in the FMI 2.0.2 Standard.

More detailed: `fmi2Struct = Union{FMU2, FMU2Component}`

  * `str::FMU2`: Mutable struct representing a FMU and all it instantiated instances in the FMI 2.0.2 Standard.
  * `str::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `state::fmi2FMUstate`: Argument `state` is a pointer to a data structure in the FMU that saves the internal FMU state of the actual or a previous time instant.

# Returns

  * `serializedState:: Array{fmi2Byte}`: Return `serializedState` contains the copy of the serialized data referenced by the pointer FMUstate

# Source

  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 Platform Dependent Definitions (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 Status Returned by Functions
  * FMISpec2.0.2[p.25]: 2.1.8 Getting and Setting the Complete FMU State

See also [`fmi2SerializeFMUstate`](@ref).
