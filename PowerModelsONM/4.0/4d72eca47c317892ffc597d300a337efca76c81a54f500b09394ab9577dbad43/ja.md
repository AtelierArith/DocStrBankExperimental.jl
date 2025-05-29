```
constraint_mc_storage_phase_unbalance(
    pm::AbstractUnbalancedPowerModel,
    nw::Int,
    i::Int,
    connections::Vector{Int},
    unbalance_factor::Real
)
```

各フェーズ間でストレージの入力/出力が（おおよそ）バランスが取れていることを、`unbalance_factor`によって強制します。

$$
S^{strg}_{i,c} \geq S^{strg}_{i,d} - f^{unbal} \left( -d^{on}_i S^{strg}_{i,d} + c^{on}_i S^{strg}_{i,d} \right) \forall c,d \in C
S^{strg}_{i,c} \leq S^{strg}_{i,d} + f^{unbal} \left( -d^{on}_i S^{strg}_{i,d} + c^{on}_i S^{strg}_{i,d} \right) \forall c,d \in C
$$
