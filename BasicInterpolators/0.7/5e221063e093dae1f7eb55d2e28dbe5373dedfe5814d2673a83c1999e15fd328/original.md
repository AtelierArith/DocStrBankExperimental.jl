```
CubicSplineInterpolator(x, y, dy₁, dyₙ, boundaries=StrictBoundaries())
```

Construct a `CubicSplineInterpolator` for the points defined by coordinates `x` and values `y`. This constructor creates a clamped spline, where the first derivatives at the boundaries are set by `dy₁` and `dyₙ`.
