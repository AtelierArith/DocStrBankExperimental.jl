```
CaptureFlueGas{T} <: CaptureData{T}
```

Capture the proxy CO₂ instance but not the energy usage related emissions and the process emissions. Does not require `emissions` as input, but can be supplied.

# Fields

  * **`emissions::Dict{ResourceEmit, T}`** are the emissions per unit produced.
  * **`co2_capture::Float64`** is the CO₂ capture rate.
