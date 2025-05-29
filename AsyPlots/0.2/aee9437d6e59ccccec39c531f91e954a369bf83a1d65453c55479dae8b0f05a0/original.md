```
Polygon3D(points;pen=Pen(),
                 fillpen=Pen(color="white"),
                 spline=false)
```

A graphics primitive representing a three-dimensional polygon

`points` may be an Array of `Vec3`s or an Array of 3-tuples.

# Examples

```julia-repl
julia> Polygon3D([(0,0,0),(1,0,0),(1,1,0)];pen="MidnightBlue")
```
