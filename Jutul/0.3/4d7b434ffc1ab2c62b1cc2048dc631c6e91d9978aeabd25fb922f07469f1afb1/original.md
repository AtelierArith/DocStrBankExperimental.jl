```
plot_mesh(mesh)
plot_mesh(mesh;
    cells = nothing,
    faces = nothing,
    boundaryfaces = nothing,
    outer = false,
    color = :lightblue,
)
```

Plot a `mesh` with uniform colors. Optionally, indices `cells`, `faces` or `boundaryfaces` can be passed to limit the plotting to a specific selection of entities.
