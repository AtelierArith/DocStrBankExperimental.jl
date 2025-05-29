```
mutable struct TGTypeII <: TurbineGov
    R::Float64
    T1::Float64
    T2::Float64
    τ_limits::MinMax
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

Parameters of a Turbine Governor Type II

# Arguments

  * `R::Float64`: Droop parameter, validation range: `(0, nothing)`
  * `T1::Float64`: Transient gain time constant, validation range: `(0, nothing)`
  * `T2::Float64`: Power fraction time constant, validation range: `(0, nothing)`
  * `τ_limits::MinMax`: Power into the governor limits
  * `P_ref::Float64`: (default: `1.0`) Reference Power Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the TGTypeI model are:

```
x_g1: lead-lag state
```

  * `n_states::Int`: (**Do not modify.**) TGTypeII has 1 state
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
