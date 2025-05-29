```
mutable struct PSSSimple <: PSS
    K_ω::Float64
    K_p::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

Parameters of a PSS that returns a proportional droop voltage to add to the reference for the AVR

# Arguments

  * `K_ω::Float64`: Proportional gain for frequency, validation range: `(0, nothing)`
  * `K_p::Float64`: Proportional gain for active power, validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) PSSSimple has no [states](@ref S)
  * `n_states::Int`: (**Do not modify.**) PSSSimple has no states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
