```
function objective_mc_variable_pg_cost(
    pm::_PMD.AbstractUnbalancedPowerModel
)
```

pg*cost変数と制約を追加します（PMDからコピーし、TD発電機との微分を可能にするために修正されました（...*dist））。
