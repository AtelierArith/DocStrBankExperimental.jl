```
EffectsCoding([base[, levels]])
EffectsCoding(; base=nothing, levels=nothing)
```

Effects coding generates columns that code each non-base level as the deviation from the base level.  For each non-base level `x` of `variable`, a column is generated with 1 where `variable .== x` and -1 where `variable .== base`.

`EffectsCoding` is like `DummyCoding`, but using -1 for the base level instead of 0.

If `levels` are omitted or `nothing`, they are determined from the data by calling the `levels` function when constructing `ContrastsMatrix`.  If `base` is omitted or `nothing`, the first level is used as the base.

When all levels are equally frequent, effects coding generates model matrix columns that are mean centered (have mean 0).  For more than two levels the generated columns are not orthogonal.  In a regression model with an effects-coded variable, the intercept corresponds to the grand mean.

Also known as "sum coding" or "simple coding". Note though that the default in R and SPSS is to use the *last* level as the base. Here we use the *first* level as the base, for consistency with other coding systems.

# Examples

```julia
julia> StatsModels.ContrastsMatrix(EffectsCoding(), ["a", "b", "c", "d"]).matrix
4×3 Array{Float64,2}:
 -1.0  -1.0  -1.0
  1.0   0.0   0.0
  0.0   1.0   0.0
  0.0   0.0   1.0
```
