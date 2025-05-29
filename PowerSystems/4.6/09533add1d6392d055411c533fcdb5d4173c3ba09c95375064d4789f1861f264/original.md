```
mutable struct PSSFixed <: PSS
    V_pss::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

Parameters of a PSS that returns a fixed voltage to add to the reference for the AVR

# Arguments

  * `V_pss::Float64`: Fixed voltage stabilization signal in pu ([`DEVICE_BASE`](@ref per_unit)), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) PSSFixed has no [states](@ref S)
  * `n_states::Int`: (**Do not modify.**) PSSFixed has no states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
