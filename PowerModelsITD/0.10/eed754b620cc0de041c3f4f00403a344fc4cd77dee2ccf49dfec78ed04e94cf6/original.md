```
function objective_mc_variable_pg_cost(
    pm::_PMD.AbstractUnbalancedIVRModel
)
```

Adds pg*cost variables and constraints (IVR formulation) (Copied from PMD and modified to allow differentiation with TD gens (...*dist)).
