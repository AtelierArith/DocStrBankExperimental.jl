```
mutable struct BaseMachine <: Machine
    R::Float64
    Xd_p::Float64
    eq_p::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

Parameters of a Classic Machine: GENCLS in PSSE and PSLF

# Arguments

  * `R::Float64`: Resistance after EMF in machine per unit, validation range: `(0, nothing)`
  * `Xd_p::Float64`: Reactance after EMF in machine per unit, validation range: `(0, nothing)`
  * `eq_p::Float64`: Fixed EMF behind the impedance, validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) BaseMachine has no [states](@ref S)
  * `n_states::Int`: (**Do not modify.**) BaseMachine has no states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
