```
SplineApproximations
```

Module for function approximation using splines.

The general idea is to find the spline $g(x)$ in a given spline space that best approximates a known function $f(x)$. In other words, given a predefined [`BSplineBasis`](@ref), the objective is to find some appropriate B-spline coefficients such that the resulting spline appropriately approximates $f$. Different approximation approaches are implemented, trading accuracy and speed.
