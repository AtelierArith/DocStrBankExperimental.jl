```
total_degree(
    F::System;
    parameters = nothing,
    gamma = cis(2π * rand()),
    tracker_options = TrackerOptions(),
    endgame_options = EndgameOptions(),
)
```

Solve the system `F` using a total degree homotopy. This returns a path tracker ([`EndgameTracker`](@ref) or [`OverdeterminedTracker`](@ref)) and an iterator to compute the start solutions. If the system `F` has declared `variable_groups` then a multi-homogeneous a start system following [^Wam93] will be constructed.

[^Wam93]: An efficient start system for multi-homogeneous polynomial continuation, Wampler, C.W. Numer. Math. (1993) 66: 517. https://doi.org/10.1007/BF01385710
