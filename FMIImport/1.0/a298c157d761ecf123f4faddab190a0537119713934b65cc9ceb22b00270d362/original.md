```
fmi2GetDerivatives(c::FMU2Component)
```

Compute state derivatives at the current time instant and for the current states.

# Arguments

  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.

# Returns

  * `derivatives::Array{fmi2Real}`: Returns an array of `fmi2Real` values representing the `derivatives` for the current states. The ordering of the elements of the derivatives vector is identical to the ordering of the state

vector.

# Source

  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 Platform Dependent Definitions (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 Status Returned by Functions
  * FMISpec2.0.2[p.83]: 3.2.2 Evaluation of Model Equations

See also [`fmi2GetDerivatives!`](@ref).
