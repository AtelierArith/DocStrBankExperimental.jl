```
fmi3GetContinuousStates(c::FMU3Instance)
```

Return the new (continuous) state vector x

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.

# Returns

  * `x::Array{fmi3Float64}`: Returns an array of `fmi3Float64` values representing the new continuous state vector `x`.

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 Platform Dependent Definitions
  * FMISpec3.0: 2.3.3. State: Initialization Mode

See also [`fmi3GetContinuousStates`](@ref).
