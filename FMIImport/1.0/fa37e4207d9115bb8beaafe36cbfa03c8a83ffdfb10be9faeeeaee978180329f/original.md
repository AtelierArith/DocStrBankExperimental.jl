```
fmi2GetEventIndicators(c::FMU2Component)
```

Returns the event indicators of the FMU

# Arguments

  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.

# Returns

  * `eventIndicators::Array{fmi2Real}`:The event indicators are returned as a vector represented by an array of "fmi2Real" values.

# Source

  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 Platform Dependent Definitions (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 Status Returned by Functions
  * FMISpec2.0.2[p.83]: 3.2.2 Evaluation of Model Equations

See also [`fmi2GetEventIndicators!`](@ref).
