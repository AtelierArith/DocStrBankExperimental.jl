```
constraint_flow_conservation(
    wm::AbstractWaterModel,
    i::Int;
    nw::Int=nw_id_default
)
```

ノード `i` およびネットワーク内のサブネットワーク（または時間）インデックス `nw` で体積流量（およびそれに伴う質量）が保存されることを保証する制約を追加するための制約テンプレートです。ここで、`wm` は WaterModels オブジェクトです。
