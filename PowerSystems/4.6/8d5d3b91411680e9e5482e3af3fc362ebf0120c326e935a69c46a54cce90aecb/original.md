```
mutable struct RLFilter <: Filter
    rf::Float64
    lf::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of RL series filter in algebraic representation

# Arguments

  * `rf::Float64`: Series resistance in p.u. of converter filter to the grid, validation range: `(0, nothing)`
  * `lf::Float64`: Series inductance in p.u. of converter filter to the grid, validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) RLFilter has zero [states](@ref S)
  * `n_states::Int`: (**Do not modify.**) RLFilter has zero states
