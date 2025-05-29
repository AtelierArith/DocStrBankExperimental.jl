```
mutable struct TGSimple <: TurbineGov
    d_t::Float64
    Tm::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

Parameters of a Simple one-state Turbine Governor

# Arguments

  * `d_t::Float64`: Inverse Droop parameter, validation range: `(0, nothing)`
  * `Tm::Float64`: Turbine Governor Low-Pass Time Constant [s], validation range: `(0, nothing)`
  * `P_ref::Float64`: (default: `1.0`) Reference Power Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the TGSimple model are:

```
τm: mechanical torque
```

  * `n_states::Int`: (**Do not modify.**) TGSimple has 1 state
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
