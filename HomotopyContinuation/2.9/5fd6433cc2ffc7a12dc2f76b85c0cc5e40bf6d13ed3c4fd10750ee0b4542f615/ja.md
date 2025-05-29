```
track(endgame_tracker::EndgameTracker, x::AbstractVector, t::Real = 1.0;
      path_number = nothing, debug = false)
```

与えられた開始解 `x` を `t` から `0` に向かって指定された `endgame_tracker` を使用して追跡します。 [`PathResult`](@ref) を返します。

```
track(endgame_tracker::EndgameTracker, r::PathResult, t::Real = 1.0;
      path_number = nothing, debug = false)
```

与えられた `endgame_tracker` を使用して `t` から `0` に向かって `solution(r)` を追跡します。
