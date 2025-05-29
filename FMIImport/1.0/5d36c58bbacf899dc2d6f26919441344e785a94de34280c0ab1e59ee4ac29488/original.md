```
fmi2GetFMUstate(c::FMU2Component)
```

Makes a copy of the internal FMU state and returns a pointer to this copy.

# Arguments

  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.

# Returns

  * Return `state` is a pointer to a copy of the internal FMU state.

# Source

  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 Platform Dependent Definitions (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.25]: 2.1.8 Getting and Setting the Complete FMU State

See also [`fmi2GetFMUstate`](@ref).
