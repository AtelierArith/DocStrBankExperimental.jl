```
constraint_on_off_pump_flow(
    wm::AbstractWaterModel,
    a::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

[`constraint_on_off_pump_head`](@ref) 制約を追加するための制約テンプレートで、ポンプで接続されたノード間のヘッド差を排他的に制限し、運転中の場合はノード間のヘッド差がヘッドゲインに等しくなることを保証し、（[`constraint_on_off_pump_head_gain`](@ref) によって制約されます。ここで、`wm` は WaterModels オブジェクト、`a` はポンプのインデックス、`nw` はマルチネットワーク内のサブネットワークのインデックスです。
