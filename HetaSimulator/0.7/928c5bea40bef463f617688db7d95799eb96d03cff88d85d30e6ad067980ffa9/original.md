```
add_scenarios!(
  platform::Platform,
  df::DataFrame;
  subset::AbstractVector{P} = Pair{Symbol, Symbol}[]
) where P <: Pair{Symbol, Symbol}
```

Adds a new `Scenario` to the `Platform`

Arguments:

  * `platform` : platform of [`Platform`](@ref) type
  * `df` : `DataFrame` with scenarios setup, typically obtained with [`read_scenarios`](@ref) function
  * `subset` : subset of scenarios which will be added to the `platform`. Default `Pair{Symbol, Symbol}[]` adds all scenarios from the `df`
