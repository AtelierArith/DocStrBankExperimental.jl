```
midpoints(body::Body[;axes=:inertial]) -> Tuple{Vector{Float64},Vector{Float64}}
```

ボディ `body` の周囲の面の x および y 中点を計算します。ボディの現在の `x` および `y` 座標（慣性空間で、`axes=:inertial` の場合）または参照 `x̃` および `ỹ` 座標（ボディ固定空間で、`axes=:body` の場合）に端点があります。例えば、面 1 は点 1 と 2 の間の面に対応します。

`body` が `BodyList` の場合、各構成ボディごとに差を別々に計算します。
