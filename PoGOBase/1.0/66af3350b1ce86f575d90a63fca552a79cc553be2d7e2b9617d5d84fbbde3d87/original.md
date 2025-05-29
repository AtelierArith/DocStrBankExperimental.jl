```
league_max_level(poke::Pokemon, league_cp::Int; level_limit=50.0) → level, cp
league_max_level(poke::Pokemon, level::Real, league_cp::Int; level_limit=50.0) → level, cp
league_max_level(name::AbstractString, ivs, level, league_cp::Int; level_limit=50.0) → level, cp
```

Return the maximum `level` and corresponding `cp` to stay at or below `league_cp`. This errors if `poke.level` is already too high, although you can manually supply an alternate `level` if you wish (1.0 is a good choice as it enables the most opportunities).
