```
run_node!(
    node::NetworkNode, climate::Climate;
    inflow=nothing, extraction=nothing, exchange=nothing
)::Nothing
```

Run a specific node, and only that node, for all time steps.

# Arguments

  * `node` : Any Streamfall NetworkNode
  * `climate` : Climate data
  * `inflow::Union{DataFrame, Vector, Number}` : Inflow to node
  * `extraction::Union{DataFrame, Vector, Number}` : Extractions from this subcatchment
  * `exchange::Union{DataFrame, Vector, Number}` : Groundwater flux
