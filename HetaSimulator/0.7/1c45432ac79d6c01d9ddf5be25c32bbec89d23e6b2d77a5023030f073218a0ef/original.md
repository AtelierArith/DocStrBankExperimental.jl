```
sim(platform::Platform; 
  scenarios::Union{AbstractVector{Symbol}, AbstractVector{InvertedIndex{Symbol}}, Nothing} = nothing,
  kwargs...) where {C<:AbstractScenario}
```

Simulate scenarios included in platform. Returns `Vector{Pair}`.

Example: `sim(platform)`

Arguments:

  * `platform` : platform of [`Platform`](@ref) type
  * `scenarios` : `Vector` containing names of scenarios included in platform. Default value `nothing` stands for all scenarios in the platform
  * `kwargs...` : other kwargs supported by `sim(scenario_pairs::Vector{Pair})`
