```
mutable struct SingleMass <: Shaft
    H::Float64
    D::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

Parameters of single mass shaft model. Typically represents the rotor mass

# Arguments

  * `H::Float64`: Rotor inertia constant in MWs/MVA, validation range: `(0, nothing)`
  * `D::Float64`: Rotor natural damping in pu, validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
δ: rotor angle,
ω: rotor speed
```

  * `n_states::Int`: (**Do not modify.**) SingleMass has 1 state
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
