```
write_node_data(vtk::VTKGridFile, nodedata::Vector{Real}, name)
write_node_data(vtk::VTKGridFile, nodedata::Vector{<:AbstractTensor}, name)
```

Write the `nodedata` that is ordered by the nodes in the grid to `vtk`.

When `nodedata` contains `Tensors.Vec`s, each component is exported. Two-dimensional vectors are padded with zeros.

When `nodedata` contains second order tensors, the index order, `[11, 22, 33, 23, 13, 12, 32, 31, 21]`, follows the default Voigt order in Tensors.jl.
