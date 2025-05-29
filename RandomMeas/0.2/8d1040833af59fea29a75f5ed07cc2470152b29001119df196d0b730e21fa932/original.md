```
get_factorized_shadows(measurement_group::MeasurementGroup{LocalUnitaryMeasurementSetting};
                       G::Vector{Float64} = fill(1.0, measurement_group.N))
```

Compute factorized shadows for all measurement results in the provided `MeasurementGroup`.

# Arguments

  * `measurement_group::MeasurementGroup{LocalUnitaryMeasurementSetting}`: Measurement data object containing measurement results and settings.
  * `G::Vector{Float64}` (optional): Vector of `G` values for measurement error correction (default: 1.0 for all sites).

# Returns

A Array of NU*NM `FactorizedShadow` objects with dimensions.
