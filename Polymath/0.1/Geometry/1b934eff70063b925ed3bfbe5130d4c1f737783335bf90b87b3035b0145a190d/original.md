```
distance_3d(x1, y1, z1, x2, y2, z2)
distance_3d(p1, p2)
```

Calculate distance between a pair of 3D points given the coordinates.

# Examples

```julia-repl
julia> distance_3d(14, 8, 5, 17, 38, 23)
35.11409973215888

julia> p1 = Point(14, 8, 5)
Point(14, 8, 5)

julia> p2 = Point(17, 38, 23)
Point(17, 38, 23)

julia> distance_3d(p1, p2)
35.11409973215888
```
