```
variable_tank_flow(
    wm::AbstractWaterModel;
    nw::Int=nw_id_default,
    bounded::Bool=true,
    report::Bool=true
)
```

ネットワーク内のタンクに対して、サブネットワーク（または時間）インデックス `nw` での有界（デフォルト）または無限の体積流量変数を作成します。すなわち、`q_tank[i]` は `tank` の `i` に対してです。貯水池とは異なり、タンクは流入を持つことができ、これは負の量として表されます。
