```
add_cell_entries!(
    sp::AbstractSparsityPattern,
    dh::DofHandler,
    ch::Union{ConstraintHandler, Nothing} = nothing;
    keep_constrained::Bool = true,
    coupling::Union{AbstractMatrix{Bool}, Nothing}, = nothing
)
```

Add entries to the sparsity pattern `sp` corresponding to DoF couplings within the cells as described by the DofHandler `dh`.

# Keyword arguments

  * `keep_constrained`: whether or not entries for constrained DoFs should be kept (`keep_constrained = true`) or eliminated (`keep_constrained = false`) from the sparsity pattern. `keep_constrained = false` requires passing the ConstraintHandler `ch`.
  * `coupling`: the coupling between fields/components within each cell. By default (`coupling = nothing`) it is assumed that all DoFs in each cell couple with each other.
