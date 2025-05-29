```
MeasurementGroup(measurements::Vector{MeasurementData{T}}) where {T <: Union{Nothing, AbstractMeasurementSetting}}
```

Construct a `MeasurementGroup` object by inferring dimensions from a vector of `MeasurementData` objects.

# Arguments

  * `measurements::Vector{MeasurementData{T}}`: A vector of `MeasurementData` objects.

# Returns

A `MeasurementGroup` object with:

  * `N`: Inferred from the first element (assumed consistent across all elements).
  * `NU`: Number of measurement data objects.
  * `NM`: Inferred from the first element.
  * `measurements`: The provided vector.

# Example

```julia
setting1 = LocalUnitaryMeasurementSetting(4, ensemble="Haar")
results1 = rand(1:2, 10, 4)
data1 = MeasurementData(results1; measurement_setting=setting1)
setting2 = LocalUnitaryMeasurementSetting(4, ensemble="Haar")
results2 = rand(1:2, 10, 4)
data2 = MeasurementData(results2; measurement_setting=setting2)
group = MeasurementGroup([data1, data2])
```
