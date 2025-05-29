```
createRegressionSetting(formula, data)

Create a regression setting for a given formula and data
```

# Arguments

  * `formula::FormulaTerm`: A formula object describes the linear regression model.
  * `data::DataFrame`: DataFrame object holds the data

# Notes

```
Implemented methods in this packages accepts linear models as RegressionSetting objects.
This objects holds the model formula and the data used in regression estimations.
createRegressionSetting is a helper function for creating RegressionSetting objects.
```

# Examples

```julia-repl
julia> setting = createRegressionSetting(@formula(calls ~ year), phones)
RegressionSetting(calls ~ year, 24×2 DataFrame
│ Row │ year  │ calls   │
│     │ Int64 │ Float64 │
├─────┼───────┼─────────┤
│ 1   │ 50    │ 4.4     │
│ 2   │ 51    │ 4.7     │
│ 3   │ 52    │ 4.7     │
│ 4   │ 53    │ 5.9     │
│ 5   │ 54    │ 6.6     │
│ 6   │ 55    │ 7.3     │
│ 7   │ 56    │ 8.1     │
│ 8   │ 57    │ 8.8     │
│ 9   │ 58    │ 10.6    │
│ 10  │ 59    │ 12.0    │
⋮
│ 14  │ 63    │ 21.2    │
│ 15  │ 64    │ 119.0   │
│ 16  │ 65    │ 124.0   │
│ 17  │ 66    │ 142.0   │
│ 18  │ 67    │ 159.0   │
│ 19  │ 68    │ 182.0   │
│ 20  │ 69    │ 212.0   │
│ 21  │ 70    │ 43.0    │
│ 22  │ 71    │ 24.0    │
│ 23  │ 72    │ 27.0    │
│ 24  │ 73    │ 29.0    │)
```
