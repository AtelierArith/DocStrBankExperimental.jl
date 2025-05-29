```
constraint_flow_conservation(
    wm::AbstractWaterModel,
    n::Int,
    i::Int,
    pipe_fr::Array{Int,1},
    pipe_to::Array{Int,1},
    des_pipe_fr::Array{Int,1},
    des_pipe_to::Array{Int,1},
    pump_fr::Array{Int,1},
    pump_to::Array{Int,1},
    regulator_fr::Array{Int,1},
    regulator_to::Array{Int,1},
    short_pipe_fr::Array{Int,1},
    short_pipe_to::Array{Int,1},
    valve_fr::Array{Int,1},
    valve_to::Array{Int,1},
    reservoirs::Array{Int,1},
    tanks::Array{Int,1},
    dispatchable_demands::Array{Int,1},
    fixed_demand::Float64
)
```

ノード `i` とサブネットワーク（または時間）インデックス `n` において、体積流量（したがって質量）が保存されることを保証する制約を追加します。ここで、`pipe_fr`、`pipe_to` などは、それぞれノード `i` から *出る* または *入る* コンポーネントです。さらに、`reservoirs`、`tanks`、および `dispatchable_demands` は、ノード `i` におけるノードの流入および流出に変動的に寄与するノード接続コンポーネントです。最後に、`fixed_demand` はノード `i` で要求される固定の流量であり、負の値 *または* 非負の値である可能性があります。
