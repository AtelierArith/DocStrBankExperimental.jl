```
MeasurementData(measurement_results::Array{Int, 2}; measurement_setting::Union{T, Nothing} = nothing)
```

Creates a `MeasurementData` object by inferring the dimensions of the measurement results and validating the provided setting.

# Arguments

  * `measurement_results::Array{Int, 2}`: A 2D array of binary measurement results with shape `(NM, N)`.
  * `measurement_setting::Union{T <: AbstractMeasurementSetting, Nothing}` (optional): Measurement setting or `nothing` if not provided.

# Returns

A `MeasurementData` object with inferred dimensions and validated setting.

# Throws

  * `AssertionError`: If the dimensions of `measurement_results` and `measurement_setting` are inconsistent.

# Examples

```julia
# With measurement setting
setting = LocalUnitaryMeasurementSetting(4, ensemble="Haar")
results = rand(1:2, 10, 4)
data_with_setting = MeasurementData(results; measurement_setting=setting)

# Without measurement setting
data_without_setting = MeasurementData(rand(1:2, 10, 4))
```
