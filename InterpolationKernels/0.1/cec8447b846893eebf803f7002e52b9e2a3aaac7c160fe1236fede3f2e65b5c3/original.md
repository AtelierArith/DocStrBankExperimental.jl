```
CatmullRomSpline([T=Float64,] B=Flat)
```

yields an instance of the Catmull-Rom interpolation kernel for floating-point type `T` and boundary conditions `B`.

Catmull-Rom interpolation kernel is a piecewise cardinal cubic spline defined by:

```
ker(x) = ((3/2)*|x| - (5/2))*x^2 + 1             if |x| ≤ 1
         (((5/2) - (1/2)*|x|)*|x| - 4)*|x| + 2   if 1 ≤ |x| ≤ 2
         0                                       if |x| ≥ 2
```

Catmull-Rom kernel is a special case of Mitchell & Netravali kernel (see [`MitchellNetravaliSplinePrime`](@ref)).

The expression `ker'` yields a kernel instance which is the 1st derivative of the Catmull-Rom interpolation kernel `ker` (also see the constructor [`CatmullRomSplinePrime`](@ref)).
