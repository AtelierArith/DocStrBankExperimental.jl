An EquilateralTriangleGrid is an iterator that makes a grid of equilateral triangles with side length `side` positioned on a rectangular grid with `nrows` and `ncols`.

```julia
EquilateralTriangleGrid(startpoint::Point, side, nrows, ncols; up = true)
```

The first triangle is centered at `startpoint` and points up if `up` is true.

###Example

```julia
nrows = 5
ncols = 8
side = 150
eqtg = EquilateralTriangleGrid(O, side, nrows, ncols)

@show first(eqtg)
# (Point[Point(-75.0, 64.9519052838329), 
         Point(0.0, -64.9519052838329), 
         Point(75.0, 64.9519052838329)], 1)

# now you can use the iterator to generate (and draw) triangles:
for tri in eqtg
    vertices, trianglenumber = tri
    randomhue()
    poly(vertices, :fill)
end
```
