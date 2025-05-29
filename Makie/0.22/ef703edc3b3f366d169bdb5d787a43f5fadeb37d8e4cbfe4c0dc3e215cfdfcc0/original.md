```
CurveTo(c1::VecTypes, c2::VecTypes, p::VecTypes)
CurveTo(cx1::Real, cy1::Real, cx2::Real, cy2::Real, px::Real, py::Real)
```

A path command for use within a `BezierPath` which continues the current subpath with a cubic bezier curve to point `p`, with the first control point `c1` and the second control point `c2`.
