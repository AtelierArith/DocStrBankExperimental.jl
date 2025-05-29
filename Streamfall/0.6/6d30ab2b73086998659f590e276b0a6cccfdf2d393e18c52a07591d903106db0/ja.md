```
run_timestep!(
    node::GR4JNode, climate::Climate, timestep::Int;
    inflow=nothing, extraction=nothing, exchange=nothing
)
run_timestep!(
    node::GR4JNode, rain::Float64, et::Float64, ts::Int64;
    inflow=nothing, extraction=nothing, exchange=nothing
)
```

与えられたGR4Jノードを時間ステップで実行します。
