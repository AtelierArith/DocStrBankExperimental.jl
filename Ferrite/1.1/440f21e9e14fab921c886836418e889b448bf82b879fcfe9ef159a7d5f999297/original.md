```
evaluate_at_grid_nodes(dh::AbstractDofHandler, u::AbstractVector{T}, fieldname::Symbol) where T
```

Evaluate the approximated solution for field `fieldname` at the node coordinates of the grid given the Dof handler `dh` and the solution vector `u`.

Return a vector of length `getnnodes(grid)` where entry `i` contains the evaluation of the approximation in the coordinate of node `i`. If the field does not live on parts of the grid, the corresponding values for those nodes will be returned as `NaN`s.
