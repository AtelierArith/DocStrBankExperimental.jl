```
pin(pt::Point3D;
    gfunction = (p3, p2) -> circle(p2, 1, :stroke))
```

Draw a single 3D point on the current Luxor drawing.

The default graphic is a circle. You can define others using a custom gfunction, which takes two arguments: the 3D point and its 2D counterpoint.

For example, this draws a circle whose radius is larger if the point is nearer to the eye.

```
pin(p, gfunction = (p3, p2) -> begin
        d = distance(p3, eyepoint())
        circle(p2, rescale(d, 0, 300, 20, 5), :fill)
    end
    )
```

Returns the 2D point.
