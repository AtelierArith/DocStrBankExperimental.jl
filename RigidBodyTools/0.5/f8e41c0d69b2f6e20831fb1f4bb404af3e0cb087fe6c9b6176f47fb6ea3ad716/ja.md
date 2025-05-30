```
curvature(body::Body/BodyList[;axes=:inertial]) -> Vector{Float64}
```

ボディ `body` の周囲の面の現在の曲率を計算します。例えば、面 1 は点 1 と 2 の間の面に対応します。`OpenBody` の場合、これは点の数よりも要素が1つ少ないベクトルを提供します。
