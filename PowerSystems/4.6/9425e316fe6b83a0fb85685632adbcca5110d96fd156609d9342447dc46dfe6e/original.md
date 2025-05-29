```
mutable struct HydroTurbineGov <: TurbineGov
    R::Float64
    r::Float64
    Tr::Float64
    Tf::Float64
    Tg::Float64
    VELM::Float64
    gate_position_limits::MinMax
    Tw::Float64
    At::Float64
    D_T::Float64
    q_nl::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

Hydro Turbine-Governor

# Arguments

  * `R::Float64`: Permanent droop parameter, validation range: `(0, 0.1)`
  * `r::Float64`: Temporary Droop, validation range: `(0, 2)`
  * `Tr::Float64`: Governor time constant, validation range: `(eps(), 30)`
  * `Tf::Float64`: Filter Time constant, validation range: `(eps(), 0.1)`
  * `Tg::Float64`: Servo time constant, validation range: `(eps(), 1)`
  * `VELM::Float64`: gate velocity limit, validation range: `(eps(), 0.3)`
  * `gate_position_limits::MinMax`: Gate position limits
  * `Tw::Float64`: water time constant, validation range: `(eps(), 3)`
  * `At::Float64`: Turbine gain, validation range: `(0.8, 1.5)`
  * `D_T::Float64`: Turbine Damping, validation range: `(0, 0.5)`
  * `q_nl::Float64`: No-power flow, validation range: `(0, nothing)`
  * `P_ref::Float64`: (default: `1.0`) Reference Power Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the HydroTurbineGov model are:

```
x_g1: filter_output,
x_g2: desired gate, 
x_g3: gate opening, 
x_g4: turbine flow
```

  * `n_states::Int`: (**Do not modify.**) HYGOV has 4 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) HYGOV has 4 [differential](@ref states_list) [states](@ref S)
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
