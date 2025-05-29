```
add_measurements!(
  platform::Platform,
  df::DataFrame;
  kwargs...
)
```

Adds measurements to `Scenario`

Arguments:

  * `platform` : platform of [`Platform`](@ref) type
  * `df` : `DataFrame` with measurements, typically obtained with [`read_measurements`](@ref) function
  * `subset` : subset of measurements which will be added to the `Scenario`. Default `Pair{Symbol, Symbol}[]` adds all measurements from the `df`
