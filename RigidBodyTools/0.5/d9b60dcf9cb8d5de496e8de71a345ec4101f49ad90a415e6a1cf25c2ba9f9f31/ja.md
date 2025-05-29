```
normalmid(body::Body/BodyList[;axes=:inertial]) -> Tuple{Vector{Float64},Vector{Float64}}
```

ボディ `body`（またはリスト `body` の各ボディ）上の周囲の端点間に形成された面の現在の法線を、慣性成分（`axes=:inertial` の場合）またはボディ固定成分（`axes=:body` の場合）で計算します。
