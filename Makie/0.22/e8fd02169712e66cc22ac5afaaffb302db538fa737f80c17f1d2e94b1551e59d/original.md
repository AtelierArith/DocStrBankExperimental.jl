```
EllipticalArc(x1::Real, y1::Real, x2::Real, y2::Real, rx::Real, ry::Real, ϕ::Real, largearc::Bool, sweepflag::Bool)
```

Construct an `EllipticalArc` using the endpoint parameterization.

`x1, y1` is the starting point and `x2, y2` the end point, `rx` and `ry` are the two ellipse radii. `ϕ` is the angle of `rx` vs the x axis.

Usually, four arcs can be constructed between two points given these ellipse parameters. One of them is chosen using two boolean flags:

If `largearc === true`, the arc will be longer than 180 degrees. If `sweepflag === true`, the arc will sweep through increasing angles.
