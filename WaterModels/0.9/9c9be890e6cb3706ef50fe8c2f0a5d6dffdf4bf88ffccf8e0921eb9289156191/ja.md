```
constraint_on_off_pump_head_gain(
    wm::AbstractWaterModel,
    a::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

[`constraint_on_off_pump_head_gain`](@ref) 制約を追加するための制約テンプレートで、稼働している場合、流量の関数としてポンプのヘッドゲインを制限します。ここで、`wm` は WaterModels オブジェクト、`a` はポンプのインデックス、`nw` はマルチネットワーク内のサブネットワークのインデックスです。
