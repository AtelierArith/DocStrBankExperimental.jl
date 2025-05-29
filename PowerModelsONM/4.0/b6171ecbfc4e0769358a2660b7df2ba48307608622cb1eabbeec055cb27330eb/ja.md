```
constraint_mc_storage_phase_unbalance_grid_following(
    pm::AbstractUnbalancedPowerModel,
    nw::Int,
    i::Int,
    connections::Vector{Int},
    unbalance_factor::Real
)
```

各フェーズ間でストレージの入力/出力が（おおよそ）バランスが取れていることを強制します。これは、グリッドフォローインバータのみに対して`unbalance_factor`によって行われます。z_inverter変数が必要です。アクティブパワーのみのモデル用のバリアントです。

$$
S^{strg}_{i,c} \geq S^{strg}_{i,d} - f^{unbal} \left( -d^{on}_i S^{strg}_{i,d} + c^{on}_i S^{strg}_{i,d} \right) \forall c,d \in C
$$
