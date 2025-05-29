```
run_node!(
    node::NetworkNode, climate::Climate, ts::Int;
    inflow=nothing, extraction=nothing, exchange=nothing
)
```

Run a specific node for a specified time step.

# Arguments

  * `node` : A node in a network
  * `climate` : Climate dataset
  * `ts` : current time step
  * `inflow` : Time series of inflows from upstream nodes.
  * `extraction` : Time series of water orders (expects column of `_releases`)
  * `exchange` : Time series of groundwater flux
