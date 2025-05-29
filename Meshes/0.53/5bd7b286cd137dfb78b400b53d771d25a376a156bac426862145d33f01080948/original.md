```
BezierCurve(points)
```

A recursive Bézier curve with control points `points`. See [https://en.wikipedia.org/wiki/Bézier_curve](https://en.wikipedia.org/wiki/Bézier_curve). A point on the curve `b` can be evaluated by calling `b(t)` with `t` between `0` and `1`. The evaluation method defaults to DeCasteljau's algorithm for accurate evaluation. Horner's method, faster with a large number of points but less precise, can be used via `b(t, Horner())`.

## Examples

```julia
BezierCurve([(0.,0.),(1.,-1.)])
```
