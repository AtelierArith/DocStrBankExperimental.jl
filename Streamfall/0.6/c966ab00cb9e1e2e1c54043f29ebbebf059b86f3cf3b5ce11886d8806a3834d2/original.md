```
run_node_with_temp!(
    s_node::IHACRESBilinearNode,
    rain::Float64,
    temp::Float64,
    inflow::Float64,
    ext::Float64,
    gw_exchange::Float64=0.0;
    current_store=nothing,
    quick_store=nothing,
    slow_store=nothing,
    gw_store=nothing
)::Tuple{Float64,Float64}
```

Run node with temperature data to calculate outflow and update state.
