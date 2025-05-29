```
constraint_on_off_valve_flow(
    wm::AbstractWaterModel,
    a::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

[`constraint_on_off_valve_flow`](@ref) 制約を追加するための制約テンプレートで、バルブの動作状況に基づいて体積流量を制限します。ここで、`wm` は WaterModels オブジェクト、`a` は流量が制限されるバルブのインデックス、`nw` は考慮されるサブネットワーク（または時間）インデックスです。
