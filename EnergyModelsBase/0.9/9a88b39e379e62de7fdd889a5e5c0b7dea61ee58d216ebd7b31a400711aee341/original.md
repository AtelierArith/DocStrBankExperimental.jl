```
EmissionsData{T<:Union{TimeProfile,Float64}} <: Data
```

Abstract type for `EmissionsData` can be used to dispatch on different types of capture configurations.

In general, the different types require the following input:

  * **`emissions::Dict{ResourceEmit, T}`** are the process emissions per capacity usage through the variable `:cap_use`. It allows for an input as `TimeProfile` or `Float64`.
  * **`co2_capture::Float64`** is the CO₂ capture rate.

# Types

  * **[`CaptureProcessEnergyEmissions`](@ref)**: Capture both the process emissions and the energy usage related emissions.
  * **[`CaptureProcessEmissions`](@ref)**: Capture the process emissions, but not the energy usage related emissions.
  * **[`CaptureEnergyEmissions`](@ref)**: Capture the energy usage related emissions, but not the process emissions. Does not require `emissions` as input.
  * **[`EmissionsProcess`](@ref)**: No capture, but process emissions are present. Does not require `co2_capture` as input, but will ignore it, if provided.
  * **[`EmissionsEnergy`](@ref)**: No capture and no process emissions. Does not require `co2_capture` or `emissions` as input, but will ignore them, if provided.
