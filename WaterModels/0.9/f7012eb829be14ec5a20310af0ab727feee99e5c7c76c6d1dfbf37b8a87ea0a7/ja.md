```
constraint_on_off_pump_power(
    wm::AbstractWaterModel,
    a::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

[`constraint_on_off_pump_power`](@ref) 制約を追加するための制約テンプレートで、稼働している場合、特定の仮定に従ってポンプの電力をモデル化します。ここで、`wm` は WaterModels オブジェクト、`a` はポンプのインデックス、`nw` はマルチネットワーク内のサブネットワークのインデックスです。
