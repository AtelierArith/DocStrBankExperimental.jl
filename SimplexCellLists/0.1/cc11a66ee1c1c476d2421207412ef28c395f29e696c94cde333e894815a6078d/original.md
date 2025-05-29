Return if an existing element in `s` is active.

```julia
isActive(s::SimplexCellList, group_idx::Integer, element_idx::Integer, element_type::Type{Simplex{N}})::Bool
```

Inactive elements are not mapped over. Elements are active by default.
