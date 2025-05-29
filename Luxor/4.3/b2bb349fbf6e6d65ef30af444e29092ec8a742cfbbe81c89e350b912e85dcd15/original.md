```
add_mesh_patch(pattern::Mesh, bezierpath::BezierPath,
    colors=Vector{Colors.Colorant})
```

Add a new patch to the mesh pattern in `pattern`.

The first three or four elements of the supplied `bezierpath` define the three or four sides of the mesh shape.

The `colors` array define the color of each corner point. Colors are reused if necessary. At least one color should be supplied.

Use `setmesh()` to select the mesh, which will be used to fill shapes.
