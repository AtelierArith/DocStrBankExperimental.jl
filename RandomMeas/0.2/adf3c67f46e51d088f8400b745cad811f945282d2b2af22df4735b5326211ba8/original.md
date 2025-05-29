```
MeasurementData(ψ::Union{MPO, MPS}, NM::Int; mode::String = "MPS/MPO", measurement_setting::Union{LocalUnitaryMeasurementSetting, ComputationalBasisMeasurementSetting, ShallowUnitaryMeasurementSetting} = nothing)
```

Returns a `MeasurementData` object by sampling `NM` projective measurements from the quantum state `ψ`.

# Arguments

  * `ψ::Union{MPO, MPS}`: The quantum state represented as a Matrix Product Operator (MPO) or Matrix Product State (MPS).
  * `NM::Int`: The number of measurement shots to simulate for each setting.
  * `mode::String` (optional): Specifies the simulation method. Options:

      * `"dense"`: Uses the dense representation.
      * `"MPS/MPO"` (default): Uses tensor network methods for memory efficiency.
  * `measurement_setting` (optional): A measurement setting object (if not provided, defaults to computational basis measurements).

# Returns

A `MeasurementData` object with the corresponding measurement results and setting.
