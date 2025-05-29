```
fmi3GetContinuousStateDerivatives(c::FMU3Instance)
```

Compute state derivatives at the current time instant and for the current states.

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.

# Returns

  * `derivatives::Array{fmi3Float64}`: Returns an array of `fmi3Float64` values representing the `derivatives` for the current states. The ordering of the elements of the derivatives vector is identical to the ordering of the state

vector.

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 Platform Dependent Definitions
  * FMISpec3.0: 3.2.1. State: Continuous-Time Mode

See also [`fmi3GetContinuousStateDerivatives`](@ref).
