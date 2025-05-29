```
mutable struct SteamTurbineGov1 <: TurbineGov
    R::Float64
    T1::Float64
    valve_position_limits::MinMax
    T2::Float64
    T3::Float64
    D_T::Float64
    DB_h::Float64
    DB_l::Float64
    T_rate::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

Steam Turbine-Governor. This model considers both TGOV1 or TGOV1DU in PSS/E

# Arguments

  * `R::Float64`: Droop parameter, validation range: `(0, 0.1)`
  * `T1::Float64`: Governor time constant, validation range: `(eps(), 0.5)`
  * `valve_position_limits::MinMax`: Valve position limits
  * `T2::Float64`: Lead Lag Lead Time constant , validation range: `(0, nothing)`
  * `T3::Float64`: Lead Lag Lag Time constant , validation range: `(eps(), 10)`
  * `D_T::Float64`: Turbine Damping, validation range: `(0, 0.5)`
  * `DB_h::Float64`: Deadband for overspeed, validation range: `(0, nothing)`
  * `DB_l::Float64`: Deadband for underspeed, validation range: `(nothing, 0)`
  * `T_rate::Float64`: Turbine Rate (MW). If zero, generator base is used, validation range: `(0, nothing)`
  * `P_ref::Float64`: (default: `1.0`) Reference Power Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the SteamTurbineGov1 model are:

```
x_g1: Valve Opening,
x_g2: Lead-lag state
```

  * `n_states::Int`: (**Do not modify.**) TGOV1 has 2 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) TGOV1 has 2 [differential](@ref states_list) [states](@ref S)
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
