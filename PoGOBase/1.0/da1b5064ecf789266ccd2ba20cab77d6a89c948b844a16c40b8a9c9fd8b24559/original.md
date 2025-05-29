```
statproduct_league(pd::Species, ivs, league_cp::Int; kwargs...) → level => (cp, statprod)
statproduct_league(name::AbstractString, ivs, league_cp::Int; kwargs...) → level => (cp, statprod)
```

Compute the `level`, `cp`, and ["stat product"](https://gostadium.club/rank-checker) for a pokemon with the given `ivs` when powered up as high as allowed by `league_cp`. The same `kwargs` as [`league_max_level`](@ref) are supported.
