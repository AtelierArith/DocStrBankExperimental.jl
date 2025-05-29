```
fmi3GetFMUState(c::FMU3Instance)
```

Makes a copy of the internal FMU state and returns a pointer to this copy.

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.

# Returns

  * Return `state` is a pointer to a copy of the internal FMU state.

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 Platform Dependent Definitions
  * FMISpec3.0: 2.2.6.4. Getting and Setting the Complete FMU State

See also [`fmi3GetFMUState`](@ref).
