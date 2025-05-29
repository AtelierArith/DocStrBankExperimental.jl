```
function constraint_distribution_power_balance_boundary(
    pmitd::AbstractPowerModelITD,
    i::Int;
    nw_pmitd::Int=nw_id_default
)
```

配電システム側の境界バスに対する一般的な電力バランス制約。
