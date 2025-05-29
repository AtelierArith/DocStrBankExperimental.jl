```
get_dof_map(space::FESpace) -> VectorDofMap
```

Returns the active dofs sorted by coordinate order, for every dimension. If `space` is a D-dimensional, scalar `FESpace`, the output index map will be a subtype of `AbstractDofMap{<:Integer,D}`. If `space` is a D-dimensional, vector-valued `FESpace`, the output index map will be a subtype of `AbstractDofMap{D+1}`.
