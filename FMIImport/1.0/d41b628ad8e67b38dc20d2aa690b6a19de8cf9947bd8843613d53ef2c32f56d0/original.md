```
fmi3GetEventIndicators(c::FMU3Instance)
```

Returns the event indicators of the FMU

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.

# Returns

  * `eventIndicators::Array{fmi3Float64}`:The event indicators are returned as a vector represented by an array of "fmi3Float64" values.

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 Platform Dependent Definitions
  * FMISpec3.0: 3.2.1. State: Continuous-Time Mode

See also [`fmi3GetEventIndicators`](@ref).
