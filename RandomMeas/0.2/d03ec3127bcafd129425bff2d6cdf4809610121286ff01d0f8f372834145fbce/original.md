```
MeasurementGroup(ψ::Union{MPO, MPS}, measurement_settings::Vector{AbstractMeasurementSetting}, NM::Int; mode::String = “MPS/MPO”, progress_bar::Bool=false)
::MeasurementGroup{T} where T <: AbstractMeasurementSetting
```

Construct a MeasurementGroup from a quantum state `ψ` by generating `NU` local measurement settings and simulating `NM` projective measurements per setting.

# Arguments

  * `ψ::Union{MPO, MPS}`: The quantum state.
  * `measurement_settings::Vector{AbstractMeasurementSetting}`: A vector with measurement settings
  * `NM::Int`: Number of measurements per setting.
  * `mode::String`: Simulation mode; defaults to “MPS/MPO”.
  * `progress_bar::Bool`: Whether to show a progress bar.

# Returns

A MeasurementGroup{T} object.
