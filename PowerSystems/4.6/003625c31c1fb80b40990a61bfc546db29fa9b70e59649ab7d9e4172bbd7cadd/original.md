```
mutable struct SEXS <: AVR
    Ta_Tb::Float64
    Tb::Float64
    K::Float64
    Te::Float64
    V_lim::MinMax
    V_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

Parameters of Simplified Excitation System Model - SEXS in PSSE

# Arguments

  * `Ta_Tb::Float64`: Ratio of lead and lag time constants, validation range: `(0, nothing)`
  * `Tb::Float64`: Lag time constant, validation range: `(eps(), nothing)`
  * `K::Float64`: Gain, validation range: `(0, nothing)`
  * `Te::Float64`: Field circuit time constant in s, validation range: `(0, nothing)`
  * `V_lim::MinMax`: Field voltage limits
  * `V_ref::Float64`: (default: `1.0`) Reference Voltage Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:	Vf: Voltage field,	Vr: Lead-lag state
  * `n_states::Int`: (**Do not modify.**) SEXS has 2 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) SEXS has 2 [differential](@ref states_list) [states](@ref S)
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
