```
league_catch_cp(catch_name::AbstractString, league_cp::Int, as_name::AbstractString = catch_name; kwargs...) → cparray
league_catch_cp(pd::Species, league_cp::Int, as::Species = pd; kwargs...) → cparray
```

Return a 3d `cparray` indexed by the IVs that returns the maximum cp to wild-catch a CP to be just at or below `league_cp` when evolved to `as_uid`.
