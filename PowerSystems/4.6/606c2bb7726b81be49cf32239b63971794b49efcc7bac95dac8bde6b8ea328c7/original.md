```
mutable struct SCRX <: AVR
    Ta_Tb::Float64
    Tb::Float64
    K::Float64
    Te::Float64
    Efd_lim::MinMax
    switch::Int
    rc_rfd::Float64
    V_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

This exciter is based on an IEEE type SCRX solid state exciter.  The output field voltage is varied by a control system to maintain the system voltage at Vref.  Please note that this exciter model has no initialization capabilities - this means that it will respond to whatever inputs it receives regardless of the state of the machine model

# Arguments

  * `Ta_Tb::Float64`: Lead input constant ratio, validation range: `(0.05, 0.3)`
  * `Tb::Float64`: Lag input constant in s, validation range: `(5, 20)`
  * `K::Float64`: Regulator Gain, validation range: `(20, 100)`
  * `Te::Float64`: Regulator Time Constant, validation range: `(0, 1)`
  * `Efd_lim::MinMax`: Field Voltage regulator limits (regulator output) (Efd*min, Efd*max)
  * `switch::Int`: Switch, validation range: `(0, 1)`
  * `rc_rfd::Float64`: Field current capability. Set = 0 for negative current capability. Typical value 10, validation range: `(0, 10)`
  * `V_ref::Float64`: (default: `1.0`) Reference Voltage Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
Vr1: First integrator,
Vr2: Second integrator
```

  * `n_states::Int`: (**Do not modify.**) SCRX has 2 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) SCRX has 2 [differential](@ref states_list) [states](@ref S)
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
