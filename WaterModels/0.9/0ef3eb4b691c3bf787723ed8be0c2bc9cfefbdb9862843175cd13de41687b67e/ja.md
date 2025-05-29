```
constraint_on_off_pump_flow(
    wm::AbstractWaterModel,
    a::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

[`constraint_on_off_pump_flow`](@ref) 制約を追加するための制約テンプレートで、ポンプの運転状況に基づいてポンプを通過する流量の量を制限します。ここで、`wm` は WaterModels オブジェクト、`a` はポンプのインデックス、`nw` はマルチネットワーク内のサブネットワークのインデックスです。
