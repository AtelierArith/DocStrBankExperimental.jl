```
make(primitive, name="unnamed")
```

`primitive` contains two arrays, an array of 3D points, and an array of faces, where each face is a list of vertex numbers.

Returns a Object.

Example

```
make(Cube, "cube")
```

returns an Object object containing an array of vertices, an array of faces, and an array of labels.

```
@draw begin
    helloworld()
    tol = 0.01
    a = []
    sethue("black")
    for t in -2pi:tol:2pi
        push!(a, Point3D((50 + cos(5t)) * cos(3t), (50 + cos(5t)) * sin(2t), sin(5t)))
    end
    Knot = make((a, []), "knot")
    pin(Knot, gfunction=(args...) -> begin
        for verts in args[1].vertices
            pin(verts)
        end
    end)
end
```

The default gfunction expects faces - if there aren't any, use a gfunction that draws vertices.
