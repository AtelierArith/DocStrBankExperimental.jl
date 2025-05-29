```
mutable struct AverageConverter <: Converter
    rated_voltage::Float64
    rated_current::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of an average converter model

# Arguments

  * `rated_voltage::Float64`: Rated voltage (V), validation range: `(0, nothing)`
  * `rated_current::Float64`: Rated current (A), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) AverageConverter has no [states](@ref S)
  * `n_states::Int`: (**Do not modify.**) AverageConverter has no states
