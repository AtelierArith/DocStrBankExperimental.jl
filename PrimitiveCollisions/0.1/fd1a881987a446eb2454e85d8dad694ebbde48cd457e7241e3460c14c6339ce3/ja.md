```julia
function invert(coldata::CollisionData{R}, current_state::State{R}) where {R}
```

`current_state`の参照フレームにおける衝突データを与えられた場合、それを反対の参照フレームに変換します。
