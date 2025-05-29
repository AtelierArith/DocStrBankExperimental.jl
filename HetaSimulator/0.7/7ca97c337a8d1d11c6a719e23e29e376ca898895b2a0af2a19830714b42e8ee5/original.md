```
sim(scenarios::AbstractVector{C}; kwargs...) where {C<:AbstractScenario}
```

Simulate multiple scenarios. Returns `Vector{Pair}`.

Example: `sim([scn1, scn2, scn3])`

Arguments:

  * `scenarios` : `Vector` containing names and scenarios of type [`Scenario`](@ref)
  * kwargs : other kwargs supported by `sim(scenario_pairs::Vector{Pair})`
