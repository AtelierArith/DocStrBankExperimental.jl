```
covratio(setting, omittedIndex)
```

Apply covariance ratio diagnostic for a given regression setting and observation index.

# Arguments

  * `setting::RegressionSetting`: A regression setting object.
  * `omittedIndex::Int`: Index of the omitted observation.

# Example

```julia-repl
julia> setting = createRegressionSetting(@formula(calls ~ year), phones);
julia> covratio(setting, 1)
1.2945913799871505
```
