```
pin(p3list::Array{Point3D, 1};
    gfunction = (p3list, p2list) ->
        poly(p2list, :stroke, close=true))
```

Draw an array of 3D points.

The default action is to draw a polygon through all the points.

The gfunction can access the 3D points as the first argument, the two 2D points in the second argument.

```
helix = [Point3D(100cos(θ), 100sin(θ), 20θ) for θ in 0:π/12:4π]
a_box = pin(helix, gfunction =
    (p3list, p2list) -> prettypoly(p2list, :stroke)
    )
```

Returns the list of 2D points.
