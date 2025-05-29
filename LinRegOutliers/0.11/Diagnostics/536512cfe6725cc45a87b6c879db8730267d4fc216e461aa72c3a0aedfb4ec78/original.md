```
hatmatrix(setting)
```

Calculate Hat matrix of dimensions n x n for a given regression setting with n observations.

# Arguments

  * `setting::RegressionSetting`: A regression setting object.

# Examples

```julia-repl
julia> reg = createRegressionSetting(@formula(calls ~ year), phones);
julia> size(hatmatrix(reg))

(24, 24)
```
