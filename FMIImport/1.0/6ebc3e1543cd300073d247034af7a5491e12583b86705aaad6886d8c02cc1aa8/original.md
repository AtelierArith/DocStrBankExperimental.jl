```
fmi3SerializedFMUStateSize(c::FMU3Instance, state::fmi3FMUState)
```

Returns the size of the byte vector in which the FMUstate can be stored.

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.
  * `state::fmi3FMUState`: Argument `state` is a pointer to a data structure in the FMU that saves the internal FMU state of the actual or a previous time instant.

# Returns

  * Return `size` is an object that safely references a value of type `Csize_t`.

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 Platform Dependent Definitions
  * FMISpec3.0: 2.2.6.4. Getting and Setting the Complete FMU State

See also [`fmi3SerializedFMUStateSize`](@ref).
