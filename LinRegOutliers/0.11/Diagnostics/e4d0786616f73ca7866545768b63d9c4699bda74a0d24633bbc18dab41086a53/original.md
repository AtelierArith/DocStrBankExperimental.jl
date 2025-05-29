```
dfbeta(setting, omittedIndex)
```

Apply DFBETA diagnostic for a given regression setting and observation index.

# Arguments

  * `setting::RegressionSetting`: A regression setting object.
  * `omittedIndex::Int`: Index of the omitted observation.

# Example

```julia-repl
julia> setting = createRegressionSetting(@formula(calls ~ year), phones);
julia> dfbeta(setting, 1)
2-element Vector{Float64}:
  9.643915678524024
 -0.14686166007904422
```
