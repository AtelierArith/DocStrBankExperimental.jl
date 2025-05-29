```
NurbsLocator

- `curve<:NurbsCurve` NURBS defined curve
- `step<:Real` buffer size around control points
- `C¹end::Bool` check if the curve is closed and C¹
```

NURBS-specific locator function. Loops through the spline sections, locating points accurately  (using inverse cubic interpolation) only if it's possible for that to be the closest section.
