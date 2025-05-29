```
SplinedBody(x,y,Δx[,closuretype=ClosedBody]) -> BasicBody
```

Using control points in `x` and `y`, create a set of points that are uniformly spaced (with spacing `Δx`) on a curve that passes through the control points. A cubic parametric spline algorithm is used. If the optional parameter `closuretype` is set to `OpenBody`, then the end points are not joined together.
