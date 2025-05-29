```
fmi2FreeFMUstate(c::FMU2Component, state::fmi2FMUstate)
```

Free the memory for the allocated FMU state

# Arguments

  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `state::fmi2FMUstate`: Argument `state` is a pointer to a data structure in the FMU that saves the internal FMU state of the actual or a previous time instant.

# Returns

  * Return singleton instance of type `Nothing`, if there is no value to return (as in a C void function) or when a variable or field holds no value.

# Source

  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 Platform Dependent Definitions (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 Status Returned by Functions
  * FMISpec2.0.2[p.25]: 2.1.8 Getting and Setting the Complete FMU State
