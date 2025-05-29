```
constraint_pipe_flow(
    wm::AbstractWaterModel,
    a::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

パイプを横切る体積流量を制限する [`constraint_pipe_flow`](@ref) 制約を追加するための制約テンプレート。ここで、`wm` は WaterModels オブジェクト、`a` は流量が制限されるパイプのインデックス、`nw` は考慮されるサブネットワーク（または時間）インデックスです。
