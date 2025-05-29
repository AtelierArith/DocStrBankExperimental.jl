```
run_timestep!(
    node::SIMHYDNode, climate::Climate, ts::Int;
    inflow=nothing, extraction=extraction, exchange=nothing
)::AbstractFloat
run_timestep!(
    node::SIMHYDNode,
    rain::F,
    et::F,
    ts::Int;
    inflow=nothing,
    extraction=nothing,
    exchange=nothing
)::F where {F<:AbstractFloat}
```

与えられたタイムステップでSIMHYDを実行します。
