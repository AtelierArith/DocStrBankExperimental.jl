```
struct CaptureProcessEmissions{T} <: CaptureData{T}

CaptureProcessEmissions(emissions::Dict{<:ResourceEmit, T}, co2_capture::Float64) where T
```

Capture the process emissions, but not the energy usage related emissions.

# Fields

  * **`emissions::Dict{ResourceEmit, T}`** are the process emissions per capacity usage through the variable `:cap_use`.
  * **`co2_capture::Float64`** is the CO₂ capture rate.
