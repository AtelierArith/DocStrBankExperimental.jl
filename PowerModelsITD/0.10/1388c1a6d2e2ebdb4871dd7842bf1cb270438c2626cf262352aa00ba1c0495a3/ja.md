```
function constraint_distribution_current_balance_boundary(
    pmitd::AbstractIVRPowerModelITD,
    i::Int;
    nw_pmitd::Int=nw_id_default
)
```

配電システム側の境界バスに対する一般的な電流バランス制約。
