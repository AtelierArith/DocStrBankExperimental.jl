```
variable_demand_flow(
    wm::AbstractWaterModel;
    nw::Int=nw_id_default,
    bounded::Bool=true,
    report::Bool=true
)
```

ネットワーク内のすべての*ディスパッチ可能*な需要に対して、サブネットワーク（または時間）インデックス `nw` での無制限の体積流量需要変数を作成します。すなわち、`q_demand[i]` は `i` が `dispatchable_demand` に含まれる場合です。
