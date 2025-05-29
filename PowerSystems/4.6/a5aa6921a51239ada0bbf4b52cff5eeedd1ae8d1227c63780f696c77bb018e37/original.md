```
mutable struct FixedFrequency <: FrequencyEstimator
    frequency::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of a Fixed Frequency Estimator (i.e. no PLL)

# Arguments

  * `frequency::Float64`: (default: `1.0`) Reference Frequency (pu)
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) FixedFrequency has no [states](@ref S)
  * `n_states::Int`: (**Do not modify.**) FixedFrequency has no states
