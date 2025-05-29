```
mutable struct AVRTypeII <: AVR
    K0::Float64
    T1::Float64
    T2::Float64
    T3::Float64
    T4::Float64
    Te::Float64
    Tr::Float64
    Va_lim::MinMax
    Ae::Float64
    Be::Float64
    V_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

Parameters of an Automatic Voltage Regulator Type II -  Typical static exciter model

# Arguments

  * `K0::Float64`: Regulator Gain, validation range: `(0, nothing)`
  * `T1::Float64`: First Pole in s, validation range: `(0, nothing)`
  * `T2::Float64`: First zero in s, validation range: `(0, nothing)`
  * `T3::Float64`: First Pole in s, validation range: `(0, nothing)`
  * `T4::Float64`: First zero in s, validation range: `(0, nothing)`
  * `Te::Float64`: Field Circuit Time Constant in s, validation range: `(0, nothing)`
  * `Tr::Float64`: Voltage Measurement Time Constant in s, validation range: `(0, nothing)`
  * `Va_lim::MinMax`: Limits for pi controler `(Va_min, Va_max)`
  * `Ae::Float64`: 1st ceiling coefficient, validation range: `(0, nothing)`
  * `Be::Float64`: 2nd ceiling coefficient, validation range: `(0, nothing)`
  * `V_ref::Float64`: (default: `1.0`) Reference Voltage Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
Vf: Voltage field,
Vr1: First Lead-Lag state,
Vr2: Second lead-lag state,
Vm: Measured voltage
```

  * `n_states::Int`: (**Do not modify.**) AVR Type II has 4 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) AVR Type II has 4 [differential](@ref states_list) [states](@ref S)
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
