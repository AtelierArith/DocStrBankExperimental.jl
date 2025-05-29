```
constraint_tank_volume(
    wm::AbstractWaterModel,
    i::Int,
    nw_1::Int,
    nw_2::Int
)
```

[`constraint_tank_volume`](@ref) 制約を追加するための制約テンプレートで、タンクの体積を時間的に前方に統合します。ここで、`wm` は WaterModels オブジェクト、`i` は制約が追加されるタンクのインデックス、`nw_1` は時間的統合で考慮される最初の時間インデックス、`nw_2` は統合で考慮される隣接する（2番目の）時間インデックスです。
