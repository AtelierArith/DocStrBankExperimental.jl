```
reduce_to_subsystem(data::MeasurementData{T}, subsystem::Vector{Int}) where T <: Union{Nothing, LocalMeasurementSetting}
```

Reduce a `MeasurementData` object to a specified subsystem, preserving the measurement setting type if available.

# Arguments

  * `data::MeasurementData{T}`: The original measurement data object, where `T` is either `nothing` or a subtype of `LocalMeasurementSetting`.
  * `subsystem::Vector{Int}`: A vector of site indices (1-based) specifying the subsystem to retain. Each index must be between 1 and `data.N`.

# Returns

A new `MeasurementData{T}` object with:

  * The measurement results reduced from dimensions `(NM, N)` to `(NM, |subsystem|)`.
  * The measurement setting reduced accordingly (if one is provided), or remaining as `nothing`.

# Example

```julia
# Suppose `data` is a MeasurementData object with N = 4.
# To retain only sites 1 and 3:
reduced_data = reduce_to_subsystem(data, [1, 3])
```
