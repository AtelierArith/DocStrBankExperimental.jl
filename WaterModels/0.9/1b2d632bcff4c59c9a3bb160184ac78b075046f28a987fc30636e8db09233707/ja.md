```
constraint_on_off_des_pipe_head(
    wm::AbstractWaterModel,
    a::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

設計パイプ間の水頭差を制限する [`constraint_on_off_des_pipe_head`](@ref) 制約を追加するための制約テンプレート。ここで、`wm` は WaterModels オブジェクト、`a` は設計パイプのインデックス、`nw` はマルチネットワーク内のサブネットワークのインデックスです。
