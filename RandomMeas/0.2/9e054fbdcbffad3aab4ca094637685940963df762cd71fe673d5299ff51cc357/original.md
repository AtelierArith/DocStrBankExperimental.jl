```
MeasurementData{T}
```

A container for measurement data and settings obtained in actual or simulated quantum experiments.

# Fields

  * `N::Int`: Number of sites (qubits).
  * `NM::Int`: Number of measurements per setting.
  * `measurement_results::Array{Int, 2}`: A 2D array of binary measurement results with dimensions `(NM, N)`.
  * `measurement_setting::T`: A measurement setting of type `T` (subtype of `AbstractMeasurementSetting`) or `nothing`.

# Type Parameter

  * `T`: The type of the measurement setting, constrained to `Union{Nothing, AbstractMeasurementSetting}`.

# Usage

Typically constructed via the provided constructors.
