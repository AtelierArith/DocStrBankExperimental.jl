```
centraldiff(bl::BodyList[;axes=:inertial]) -> Tuple{Vector{Float64},Vector{Float64}}
```

`bl`の各構成体に対して`centraldiff`を計算します。`axes=:body`の場合、ボディ固定空間の基準座標を使用します。
