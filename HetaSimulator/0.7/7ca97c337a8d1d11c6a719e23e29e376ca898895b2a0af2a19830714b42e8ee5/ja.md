```
sim(scenarios::AbstractVector{C}; kwargs...) where {C<:AbstractScenario}
```

複数のシナリオをシミュレートします。`Vector{Pair}`を返します。

例: `sim([scn1, scn2, scn3])`

引数:

  * `scenarios` : [`Scenario`](@ref)型の名前とシナリオを含む`Vector`
  * kwargs : `sim(scenario_pairs::Vector{Pair})`でサポートされている他のkwargs
