```
mutable struct TGFixed <: TurbineGov
    efficiency::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

Parameters of a fixed Turbine Governor that returns a fixed mechanical torque  given by the product of P_ref*efficiency

# Arguments

  * `efficiency::Float64`: Efficiency factor that multiplies `P_ref`, validation range: `(0, nothing)`
  * `P_ref::Float64`: (default: `1.0`) Reference Power Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) TGFixed has no [states](@ref S)
  * `n_states::Int`: (**Do not modify.**) TGFixed has no states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
