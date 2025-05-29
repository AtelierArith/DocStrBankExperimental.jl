```
dlength(body::Body/BodyList[;axes=:inertial]) -> Vector{Float64}
```

ボディ `body` の周囲の面の長さを計算します。面の端はボディの現在の `xend` および `yend` 座標（慣性空間内）にあります。例えば、面 1 は端点 1 と 2 の間の面に対応します。`axes=:body` の場合、ボディ固定空間内の基準座標を使用します。
