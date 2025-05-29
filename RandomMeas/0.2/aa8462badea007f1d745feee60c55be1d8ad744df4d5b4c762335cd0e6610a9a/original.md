```
MeasurementGroup{T}
```

A container for a group of measurement data objects used in actual or simulated quantum experiments.

# Fields

  * `N::Int`: Number of sites (qubits).
  * `NU::Int`: Number of measurement data objects.
  * `NM::Int`: Number of measurements per setting.
  * `measurements::Vector{MeasurementData{T}}`: A vector of measurement data objects.

# Type Parameter

  * `T`: The type of the measurement setting for each measurement data object, constrained to `Union{Nothing, AbstractMeasurementSetting}`.

# Usage

Typically constructed via one of the provided constructors.

# Example

```julia
# Assume setting1 and setting2 are valid measurement settings
data1 = MeasurementData(results1; measurement_setting=setting1)
data2 = MeasurementData(results2; measurement_setting=setting2)
group = MeasurementGroup([data1, data2])
```
