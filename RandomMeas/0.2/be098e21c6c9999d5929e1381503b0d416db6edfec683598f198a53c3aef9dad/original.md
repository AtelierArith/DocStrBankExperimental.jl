```
get_factorized_shadows(measurement_data::MeasurementData{LocalUnitaryMeasurementSetting};
                       G::Vector{Float64} = fill(1.0, measurement_data.N))
```

Compute factorized shadows for all measurement results in the provided `MeasurementData`.

# Arguments

  * `measurement_data::MeasurementData{LocalUnitaryMeasurementSetting}`: Measurement data object containing measurement results and settings.
  * `G::Vector{Float64}` (optional): Vector of `G` values for measurement error correction (default: 1.0 for all sites).

# Returns

A Vector of NM `FactorizedShadow` objects with dimensions.
