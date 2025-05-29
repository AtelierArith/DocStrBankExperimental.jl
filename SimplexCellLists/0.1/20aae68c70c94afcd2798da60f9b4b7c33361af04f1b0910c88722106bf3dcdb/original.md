Add a new element to `s`, and return its element index:

```julia
addElement!(s::SimplexCellList, group_idx::Integer, element::Simplex{N})::Int32
```

The new element will be pushed to the end of the specified group.
