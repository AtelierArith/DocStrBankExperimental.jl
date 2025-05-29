Re-activate an existing element in `s`

```julia
activate!(s::SimplexCellList, group_idx::Integer, element_idx::Integer, element_type::Type{Simplex{N}})::Nothing
```

Inactive elements are not mapped over. Elements are active by default.
