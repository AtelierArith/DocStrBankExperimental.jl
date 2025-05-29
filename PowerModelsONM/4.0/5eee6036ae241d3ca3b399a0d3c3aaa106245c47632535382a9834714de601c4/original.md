```
variable_block_indicator(
    pm::AbstractUnbalancedPowerModel;
    nw::Int=nw_id_default,
    relax::Bool=false,
    report::Bool=true
)
```

Create variables for block status by load block, $z^{bl}_i\in{0,1}~\forall i \in B$, binary if `relax=false`. Variables will appear in solution if `report=true`.
