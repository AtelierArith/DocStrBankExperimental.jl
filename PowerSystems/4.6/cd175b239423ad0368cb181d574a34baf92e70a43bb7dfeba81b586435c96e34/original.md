```
mutable struct ZeroOrderBESS <: DCSource
    rated_voltage::Float64
    rated_current::Float64
    battery_voltage::Float64
    battery_resistance::Float64
    dc_dc_inductor::Float64
    dc_link_capacitance::Float64
    fs::Float64
    kpv::Float64
    kiv::Float64
    kpi::Float64
    kii::Float64
    Vdc_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters for the DC-side with a Battery Energy Storage System from ["Grid-Coupled Dynamic Response of Battery-Driven Voltage Source Converters."](https://arxiv.org/abs/2007.11776)

# Arguments

  * `rated_voltage::Float64`: Rated voltage (V), validation range: `(0, nothing)`
  * `rated_current::Float64`: Rated current (A), validation range: `(0, nothing)`
  * `battery_voltage::Float64`: battery voltage in pu ([`DEVICE_BASE`](@ref per_unit)), validation range: `(0, nothing)`
  * `battery_resistance::Float64`: Battery resistance in pu ([`DEVICE_BASE`](@ref per_unit)), validation range: `(0, nothing)`
  * `dc_dc_inductor::Float64`: DC/DC inductance in pu ([`DEVICE_BASE`](@ref per_unit)), validation range: `(0, nothing)`
  * `dc_link_capacitance::Float64`: DC-link capacitance in pu ([`DEVICE_BASE`](@ref per_unit)), validation range: `(0, nothing)`
  * `fs::Float64`: DC/DC converter switching frequency (kHz), validation range: `(0, nothing)`
  * `kpv::Float64`: voltage controller proportional gain, validation range: `(0, nothing)`
  * `kiv::Float64`: voltage controller integral gain, validation range: `(0, nothing)`
  * `kpi::Float64`: current controller proportional gain, validation range: `(0, nothing)`
  * `kii::Float64`: current controller integral gain, validation range: `(0, nothing)`
  * `Vdc_ref::Float64`: (default: `1.1`) Reference DC-Voltage Set-point in pu ([`DEVICE_BASE`](@ref per_unit)), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the ZeroOrderBESS model are:

```
v_dc: DC-link voltage,
i_b: Battery current,
 ν: integrator state of the voltage controller,
 ζ: integrator state of the PI current controller
```

  * `n_states::Int`: (**Do not modify.**) ZeroOrderBESS has 4 states
