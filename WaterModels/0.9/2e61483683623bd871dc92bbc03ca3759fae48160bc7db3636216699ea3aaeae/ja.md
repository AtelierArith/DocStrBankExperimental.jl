```
constraint_tank_volume(
    wm::AbstractWaterModel,
    n_1::Int,
    n_2::Int,
    i::Int,
    time_step::Float64
)
```

タンクの体積を時間的に前方に統合する制約を追加します。ここで、`wm`はWaterModelsオブジェクト、`n_1`はマルチネットワーク内のサブネットワークのインデックス、`n_2`は`n_1`に対して時間的に前方にある別のサブネットワークのインデックス、`i`はタンクのインデックス、`time_step`はネットワーク`n_1`から`n_2`までの間隔の時間ステップです。
