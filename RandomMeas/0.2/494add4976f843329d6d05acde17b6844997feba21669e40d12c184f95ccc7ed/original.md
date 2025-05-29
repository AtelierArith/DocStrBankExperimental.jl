```
MeasurementGroup(ψ::Union{MPO, MPS}, NU::Int, NM::Int, depth::Int; mode::String = “MPS/MPO”, progress_bar::Bool=false)
```

::MeasurementGroup{ShallowUnitaryMeasurementSetting}

Construct a MeasurementGroup from a quantum state `ψ` by generating `NU` shallow measurement settings and simulating `NM` measurements per unitary.

# Arguments

  * `ψ::Union{MPO, MPS}`: The quantum state.
  * `NU::Int`: Number of measurement data objects to generate.
  * `NM::Int`: Number of measurements per setting.
  * `depth::Int`: Circuit depth for shallow settings.
  * `mode::String`: Simulation mode; defaults to “MPS/MPO”.
  * `progress_bar`::Bool: Whether to show a progress bar.

# Returns

A MeasurementGroup{ShallowUnitaryMeasurementSetting} object.
