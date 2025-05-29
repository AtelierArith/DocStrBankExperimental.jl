```
variable_switch_state(
    pm::AbstractUnbalancedPowerModel;
    nw::Int=nw_id_default,
    report::Bool=true,
    relax::Bool=false
)
```

Create variables for switch state (open/close) variables, $\gamma_i\in{0,1}~\forall i \in S$, binary if `relax=false`. Variables for non-dispatchable switches will be constants, rather than `VariableRef`. Variables will appear in solution if `report=true`.
