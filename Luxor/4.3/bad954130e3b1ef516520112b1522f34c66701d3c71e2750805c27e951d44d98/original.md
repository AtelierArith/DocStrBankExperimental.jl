```
mesh(bezierpath::BezierPath,
     colors=Vector{Colors.Colorant})
```

Create a mesh. The first three or four elements of the supplied `bezierpath` define the three or four sides of the mesh shape.

The `colors` array define the color of each corner point. Colors are reused if necessary. At least one color should be supplied.

Use `setmesh()` to select the mesh, which will be used to fill shapes.

# Example

```julia
@svg begin
    bp = makebezierpath(ngon(O, 50, 4, 0, vertices=true))
    mesh1 = mesh(bp, [
        "red",
        Colors.RGB(0, 1, 0),
        Colors.RGB(0, 1, 1),
        Colors.RGB(1, 0, 1)
        ])
    setmesh(mesh1)
    box(O, 500, 500, :fill)
end
```
