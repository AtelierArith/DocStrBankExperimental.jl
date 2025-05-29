```
QuadraticSpline([T=Float64,] B=Flat)
```

yields an instance of the quadratic spline for floating-point type `T` and boundary conditions `B`.

The quadratic spline is the 3rd order (quadratic) B-spline given by:

```
ker(x) = 3/4 - x^2                   if |x| ≤ 1/2
         (1/2)*(|x| - 3/2)^2         if |x| ≤ 3/2
         0                           if |x| ≥ 3/2
```

The expression `ker'` yields a kernel instance which is the 1st derivative of the quadratic spline `ker` (also see the constructor [`QuadraticSplinePrime`](@ref)).
