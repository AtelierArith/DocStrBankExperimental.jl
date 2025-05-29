```
CardinalCubicSpline([T=Float64,] c, B=Flat)
```

yields an instance of a cardinal cubic spline interpolation kernel for floating-point type `T`, tension parameter `c` and boundary conditions `B`.

The slope at `x = ±1` is `±(c - 1)/2`.  Usually `c ≤ 1`, choosing `c = 0` yields a Catmull-Rom spline (see [`CatmullRomSpline`](@ref)), `c = 1` yields all zero tangents, `c = -1` yields a truncated approximation of a cardinal sine, `c = -1/2` yields an interpolating cubic spline with continuous second derivatives (inside its support).

The expression `ker'` yields a kernel instance which is the 1st derivative of the cardinal cubic spline `ker` (also see the constructor [`CardinalCubicSplinePrime`](@ref)).
