```
render(mesh::Mesh; normals::Bool = false, wireframe::Bool = false, kwargs...)
```

Render a `Mesh` object. This will create a new visualization (see Documentation for details). `normals = true` will draw arrows in the direction of the normal vector for each triangle in the mesh, `wireframe = true` will draw the edges of each triangle with black lines. Keyword arguments are passed to `Makie.mesh()`. The actual color of each triangle depends on the illumination of the scene but it is possible to turn this off by passing `shading = false`. This will use the exact colors specified in the `Scene` object.
