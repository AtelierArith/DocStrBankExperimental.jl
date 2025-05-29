```
CardinalCubicSplinePrime{T}(a)
```

yields a kernel instance that is the 1st derivative of the Keys cardinal cubic spline (see [`CardinalCubicSpline`](@ref)) for floating-point type `T` and parameter `a`.  This derivative is given by:

```
ker′(x) = (3(a + 2)*|x| - 2(a + 3))*x           if |x| ≤ 1
          (3a)*(|x| - 2)*(|x| - 4/3)*sign(x)    if 1 ≤ |x| ≤ 2
          0                                     if |x| ≥ 2
```
