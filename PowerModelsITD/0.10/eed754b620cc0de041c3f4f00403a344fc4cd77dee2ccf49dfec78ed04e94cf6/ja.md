```
function objective_mc_variable_pg_cost(
    pm::_PMD.AbstractUnbalancedIVRModel
)
```

pg*cost変数と制約（IVR定式化）を追加します（PMDからコピーし、TD発電機との微分を可能にするために修正されました（...*dist））。
