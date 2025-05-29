```
run_timestep!(
    node::SimpleHyModNode, climate::Climate, timestep::Int;
    inflow=nothing, extraction=nothing, exchange=nothing
)::Float64
```

与えられたHyModノードを時間ステップで実行します。
