```
FEFunction(
  fs::SingleFieldFESpace, free_values::AbstractVector, dirichlet_values::AbstractVector)
```

The resulting FEFunction will be in the space if and only if `dirichlet_values` are the ones provided by `get_dirichlet_dof_values(fs)`
