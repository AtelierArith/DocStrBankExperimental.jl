```
add_measurements!(
  scenario::Scenario,
  df::DataFrame;
  kwargs...
)
```

Adds measurements to `Scenario`

Arguments:

  * `scenario` : simulation scenario of type [`Scenario`](@ref)
  * `df` : `DataFrame` with measurements, typically obtained with [`read_measurements`](@ref) function
  * `subset` : subset of measurements which will be added to the `Scenario`. Default `Pair{Symbol, Symbol}[]` adds all measurements from the `df`
