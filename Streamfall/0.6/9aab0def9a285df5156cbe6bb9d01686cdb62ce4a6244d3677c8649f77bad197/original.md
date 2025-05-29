```
run_node!(
    sn::StreamfallNetwork, node_id::Int, climate::Climate, ts::Int64;
    inflow=nothing, extraction=nothing, exchange=nothing
)::Nothing
```

Generic run method that runs a model attached to a given node for a given timestep. Recurses upstream as needed.

# Arguments

  * `sn::StreamfallNetwork`
  * `node_id` : Node to run in the network
  * `climate` : Climate object holding rainfall and evaporation data (or temperature)
  * `ts` : Timestep to run
  * `extraction` : Water orders for each time step (defaults to nothing)
  * `exchange` : Exchange with groundwater system at each time step (defaults to nothing)
