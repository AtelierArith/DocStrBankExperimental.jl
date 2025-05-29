```
run_node!(
    node::DamNode, climate::Climate, ts::Int;
    inflow=nothing, extraction=nothing, exchange=nothing
)::Nothing
```

Run a specific node for a specified time step.

# Arguments

  * `node` : DamNode
  * `climate` : Climate dataset
  * `ts` : Current time step
  * `inflow` : Time series of inflows from any upstream node.
  * `extraction` : Time series of water orders (expects column of `_releases`)
  * `exchange` : Time series of groundwater flux
