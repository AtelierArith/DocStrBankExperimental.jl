```
arclength(bl::BodyList[;axes=:inertial]) -> Vector{Float64}
```

`bl`内の各ボディの合計アーク長を計算し、結果をベクトルにまとめます。`axes=:body`を使用する場合は、ボディ固定座標を使用します。
