```
extract_features(mapper, ics; N = 1000, show_progress = true)
```

Return a vector of the features of each initial condition in `ics` (as in [`basins_fractions`](@ref)), using the configuration of `mapper::AttractorsViaFeaturizing`. Keyword `N` is ignored if `ics isa StateSpaceSet`.
