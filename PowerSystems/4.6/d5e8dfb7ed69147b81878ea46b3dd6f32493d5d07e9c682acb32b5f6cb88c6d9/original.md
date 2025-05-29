```
mutable struct FixedDCSource <: DCSource
    voltage::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

Parameters of a Fixed DC Source that returns a fixed DC voltage

# Arguments

  * `voltage::Float64`: Voltage (V), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) FixedDCSource has no [states](@ref S)
  * `n_states::Int`: (**Do not modify.**) FixedDCSource has no states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
