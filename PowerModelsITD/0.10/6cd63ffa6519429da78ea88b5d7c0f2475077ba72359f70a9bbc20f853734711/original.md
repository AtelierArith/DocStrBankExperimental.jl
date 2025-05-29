```
function objective_mc_variable_pg_cost(
    pm::_PMD.AbstractUnbalancedPowerModel
)
```

Adds pg*cost variables and constraints (Copied from PMD and modified to allow differentiation with TD gens (...*dist)).
