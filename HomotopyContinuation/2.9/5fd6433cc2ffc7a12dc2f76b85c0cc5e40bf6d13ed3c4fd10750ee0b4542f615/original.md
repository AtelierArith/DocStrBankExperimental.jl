```
track(endgame_tracker::EndgameTracker, x::AbstractVector, t::Real = 1.0;
      path_number = nothing, debug = false)
```

Track the given start solution `x` from `t` towards `0` using the given `endgame_tracker`. Returns a [`PathResult`](@ref).

```
track(endgame_tracker::EndgameTracker, r::PathResult, t::Real = 1.0;
      path_number = nothing, debug = false)
```

Track `solution(r)` from `t` towards `0` using the given `endgame_tracker`.
