```
mutable struct TGTypeI <: TurbineGov
    R::Float64
    Ts::Float64
    Tc::Float64
    T3::Float64
    T4::Float64
    T5::Float64
    valve_position_limits::MinMax
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

Parameters of a Turbine Governor Type I

# Arguments

  * `R::Float64`: Droop parameter, validation range: `(0, nothing)`
  * `Ts::Float64`: Governor time constant, validation range: `(0, nothing)`
  * `Tc::Float64`: Servo time constant, validation range: `(0, nothing)`
  * `T3::Float64`: Transient gain time constant, validation range: `(0, nothing)`
  * `T4::Float64`: Power fraction time constant, validation range: `(0, nothing)`
  * `T5::Float64`: Reheat time constant, validation range: `(0, nothing)`
  * `valve_position_limits::MinMax`: Valve position limits in MW
  * `P_ref::Float64`: (default: `1.0`) Reference Power Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the TGTypeI model are:

```
x_g1: Governor state,
x_g2: Servo state,
x_g3: Reheat state
```

  * `n_states::Int`: (**Do not modify.**) TGTypeI has 3 states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
