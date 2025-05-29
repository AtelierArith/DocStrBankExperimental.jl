```
pin(p3_1::Point3D, p3_2::Point3D;
    gfunction = ((p3_1, p3_2), (p2_1, p2_2)) ->
        line(p2_1, p2_2, :stroke))
```

Draw two 3D points.

The default action is to draw a line between two points.

The gfunction can access the 3D points as the first argument, the two 2D points in the second argument.

```
pin(p, Point3D(50cos(θ), 50sin(θ), p.z),
    gfunction = (p3s, p2s) -> begin
        line(p2s..., :stroke)
    end)

```

Returns the two 2D points.
