```
MeasurementData(measurement_probability::MeasurementProbability{T}, NM::Int) where T <: Union{Nothing, AbstractMeasurementSetting}
```

Returns a `MeasurementData` object by sampling `NM` projective measurements based on the provided measurement probability.

# Arguments

  * `measurement_probability::MeasurementProbability`: A container with the measurement probability (an ITensor) and associated settings.
  * `NM::Int`: The number of projective measurements to sample.

# Returns

A `MeasurementData` object with dimensions inferred from the measurement probability.
