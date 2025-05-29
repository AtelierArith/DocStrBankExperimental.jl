```
DenseShadow(measurement_data::MeasurementData{LocalUnitaryMeasurementSetting}; G::Vector{Float64} = fill(1.0, size(measurement_data.N, 2)))
```

Construct a `DenseShadow` object from a MeasurementDataObject

# Arguments

  * `measurement_data::MeasurementData{LocalUnitaryMeasurementSetting}:
  * `G::Vector{Float64}` (optional): Vector of G values to account for measurement errors (default: 1.0 for all sites).

# Returns

A `DenseShadow` object.
