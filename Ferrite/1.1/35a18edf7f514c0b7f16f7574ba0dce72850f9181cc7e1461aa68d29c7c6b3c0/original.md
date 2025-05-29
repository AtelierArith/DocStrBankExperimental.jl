```
write_solution(vtk::VTKGridFile, dh::AbstractDofHandler, u::AbstractVector, suffix="")
```

Save the values at the nodes in the degree of freedom vector `u` to `vtk`. Each field in `dh` will be saved separately, and `suffix` can be used to append to the fieldname.

`u` can also contain tensorial values, but each entry in `u` must correspond to a degree of freedom in `dh`, see [`write_node_data`](@ref write_node_data) for details. Use `write_node_data` directly when exporting values that are already sorted by the nodes in the grid.
