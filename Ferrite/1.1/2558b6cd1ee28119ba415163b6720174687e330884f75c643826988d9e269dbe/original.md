```
add_interface_entries!(
    sp::SparsityPattern, dh::DofHandler, ch::Union{ConstraintHandler, Nothing};
    topology::ExclusiveTopology, keep_constrained::Bool = true,
    interface_coupling::AbstractMatrix{Bool},
)
```

Add entries to the sparsity pattern `sp` corresponding to DoF couplings on the interface between cells as described by the DofHandler `dh`.

# Keyword arguments

  * `topology`: the topology corresponding to the grid.
  * `keep_constrained`: whether or not entries for constrained DoFs should be kept (`keep_constrained = true`) or eliminated (`keep_constrained = false`) from the sparsity pattern. `keep_constrained = false` requires passing the ConstraintHandler `ch`.
  * `interface_coupling`: the coupling between fields/components across the interface.
