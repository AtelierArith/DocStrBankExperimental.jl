```
struct CaptureEnergyEmissions{T} <: CaptureData{T}

CaptureEnergyEmissions(emissions::Dict{<:ResourceEmit, T}, co2_capture::Float64) where T
CaptureEnergyEmissions(co2_capture::Float64)
```

Capture the energy usage related emissions, but not the process emissions. Does not require `emissions` as input, but can be supplied.

# Fields

  * **`emissions::Dict{ResourceEmit, T}`** are the process emissions per capacity usage through the variable `:cap_use`.
  * **`co2_capture::Float64`** is the CO₂ capture rate.
