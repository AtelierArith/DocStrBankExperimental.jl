```
plot_cell_data(mesh::JutulMesh, data::Vector; kwarg...)
plot_cell_data(mesh, data;
    cells = nothing,
    faces = nothing,
    boundaryfaces = nothing
)
```

Plot cell-wise values (as a vector) on the mesh. Optionally, indices `cells`, `faces` or `boundaryfaces` can be passed to limit the plotting to a specific selection of entities.
