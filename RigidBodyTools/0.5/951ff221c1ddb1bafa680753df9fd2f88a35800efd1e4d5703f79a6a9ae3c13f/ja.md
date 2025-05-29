```
centraldiff(body::Body[;axes=:inertial]) -> Tuple{Vector{Float64},Vector{Float64}}
```

ボディ `body` の座標の円形中心差分を計算します（またはリスト `body` の各ボディに対して）。`axes=:body` の場合、ボディ固定空間の基準座標を使用します。
