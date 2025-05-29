```
fmi2GetEventIndicators!(c::FMU2Component, eventIndicators::AbstractArray{fmi2Real})
```

Returns the event indicators of the FMU.

# Arguments

  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `eventIndicators::AbstractArray{fmi2Real}`:The event indicators are in an AbstractArray represented by an array of "fmi2Real" values.

# Returns

# Source

  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 Platform Dependent Definitions (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 Status Returned by Functions
  * FMISpec2.0.2[p.83]: 3.2.2 Evaluation of Model Equations
