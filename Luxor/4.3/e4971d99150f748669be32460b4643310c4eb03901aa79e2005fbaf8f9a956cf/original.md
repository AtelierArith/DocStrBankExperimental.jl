```
mesh(points::Array{Point}, colors=Vector{Colors.Colorant})
```

Create a mesh.

The first three or four sides of the supplied `points` polygon define the three or four sides of the mesh shape.

The `colors` array define the color of each corner point. Colors are reused if necessary. At least one color should be supplied.

# Example

```julia
@svg begin
    pl = ngon(O, 250, 3, pi/6, vertices=true)
    mesh1 = mesh(pl, [
        "purple",
        Colors.RGBA(0.0, 1.0, 0.5, 0.5),
        "yellow"
        ])
    setmesh(mesh1)
    setline(180)
    ngon(O, 250, 3, pi/6, :strokepreserve)
    setline(5)
    sethue("black")
    strokepath()
end
```
