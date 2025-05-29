```
FEFunction(
  fs::SingleFieldFESpace, free_values::AbstractVector, dirichlet_values::AbstractVector)
```

結果として得られるFEFunctionは、`dirichlet_values`が`get_dirichlet_dof_values(fs)`によって提供されるものである場合に限り、その空間に存在します。
