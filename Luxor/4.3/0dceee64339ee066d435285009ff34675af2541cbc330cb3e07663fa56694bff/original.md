```
rule1(point1::Point, point2::Point;
    boundingbox=BoundingBox(),
    vertices=false)
```

Draw a straight line passing through points `point1` and `point2`.

```julia
rule(Point(10, 10), Point(30, -30))
```

Supply a BoundingBox to restrict the ruled lines to a rectangular area.

Returns the two end points in a Vector.

Use `vertices=true` to just return the end points, without drawing a line.
