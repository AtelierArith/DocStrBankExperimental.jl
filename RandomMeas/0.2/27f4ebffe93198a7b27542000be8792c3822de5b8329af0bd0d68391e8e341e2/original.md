```
get_dense_shadows(measurement_group::MeasurementGroup{LocalUnitaryMeasurementSetting};
                  G::Vector{Float64} = fill(1.0, N),
                  number_of_ru_batches::Int = NU)
```

Compute dense shadows for the provided measurement data in batches.

# Arguments

  * `measurement_group::MeasurementGroup{LocalUnitaryMeasurementSetting}`: Measurement data object.
  * `G::Vector{Float64}` (optional): Vector of G values for robustness (default: 1.0 for all sites).
  * `number_of_ru_batches::Int` (optional): Number of random unitary batches (default: `NU`).

# Returns

A Vector of `DenseShadow` objects.
