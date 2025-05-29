```
constraint_on_off_des_pipe_flow(
    wm::AbstractWaterModel,
    a::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

設計パイプを通過する流量を制限する [`constraint_on_off_des_pipe_flow`](@ref) 制約を追加するための制約テンプレート。ここで、`wm` は WaterModels オブジェクト、`a` は設計パイプのインデックス、`nw` はマルチネットワーク内のサブネットワークのインデックスです。
