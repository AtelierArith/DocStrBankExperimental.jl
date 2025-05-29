```
MeasurementGroup(ψ::Union{MPO, MPS}, NU::Int, NM::Int; mode::String = “MPS/MPO”, progress_bar::Bool=false)
```

::MeasurementGroup{LocalUnitaryMeasurementSetting}

Construct a MeasurementGroup from a quantum state `ψ` by generating `NU` local measurement settings and simulating `NM` projective measurements per setting.

# Arguments

  * `ψ::Union{MPO, MPS}`: The quantum state.
  * `NU::Int`: Number of measurement data objects to generate.
  * `NM::Int`: Number of measurements per setting.
  * `mode::String`: Simulation mode; defaults to “MPS/MPO”.
  * `progress_bar::Bool`: Whether to show a progress bar.

# Returns

A MeasurementGroup{LocalUnitaryMeasurementSetting} object.
