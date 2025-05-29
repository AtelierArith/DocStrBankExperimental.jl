```
mutable struct VoltageModeControl <: InnerControl
    kpv::Float64
    kiv::Float64
    kffv::Float64
    rv::Float64
    lv::Float64
    kpc::Float64
    kic::Float64
    kffi::Float64
    ωad::Float64
    kad::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of an inner loop current control PID using virtual impedance based on ["A Virtual Synchronous Machine implementation for distributed control of power converters in SmartGrids."](https://doi.org/10.1016/j.epsr.2015.01.001)

# Arguments

  * `kpv::Float64`: voltage controller proportional gain, validation range: `(0, nothing)`
  * `kiv::Float64`: voltage controller integral gain, validation range: `(0, nothing)`
  * `kffv::Float64`: Binary variable to enable feed-forward gain of voltage, validation range: `(0, nothing)`
  * `rv::Float64`: virtual resistance, validation range: `(0, nothing)`
  * `lv::Float64`: virtual inductance, validation range: `(0, nothing)`
  * `kpc::Float64`: current controller proportional gain, validation range: `(0, nothing)`
  * `kic::Float64`: current controller integral gain, validation range: `(0, nothing)`
  * `kffi::Float64`: Binary variable to enable feed-forward gain of current, validation range: `(0, nothing)`
  * `ωad::Float64`: active damping filter cutoff frequency (rad/sec), validation range: `(0, nothing)`
  * `kad::Float64`: active damping gain, validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the VoltageModeControl model are:

```
ξd_ic: d-axis integrator state of the PI voltage controller,
ξq_ic: q-axis integrator state of the PI voltage controller,
γd_ic: d-axis integrator state of the PI current controller,
γq_ic: q-axis integrator state of the PI current controller,
ϕd_ic: d-axis low-pass filter of active damping,
ϕq_ic: q-axis low-pass filter of active damping
```

  * `n_states::Int`: (**Do not modify.**) VoltageModeControl has 6 states
