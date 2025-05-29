```
CatmullRomSpline{T}()
```

yields an instance of the Catmull-Rom interpolation kernel for floating-point type `T` which is assumed to be `Float64` if omitted.

Catmull-Rom interpolation kernel is a cardinal piecewise cubic spline defined by:

```
ker(x) = ((3/2)*|x| - (5/2))*x^2 + 1             if |x| ≤ 1
         (((5/2) - (1/2)*|x|)*|x| - 4)*|x| + 2   if 1 ≤ |x| ≤ 2
         0                                       if |x| ≥ 2
```

The expression `ker'` yields a kernel instance which is the 1st derivative of the Catmull-Rom interpolation kernel `ker` (also see the constructor [`CatmullRomSplinePrime`](@ref)).
