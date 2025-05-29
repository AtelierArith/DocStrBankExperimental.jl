```
CubicSpline([T=Float64,] B=Flat)
```

yields an instance of the cubic spline for floating-point type `T` and boundary conditions `B`.

The 4th order (cubic) B-spline kernel is also known as *Parzen window* or as *de la Vallée Poussin window*.   It is given by:

```
ker(x) = 2/3 + (|x|/2 - 1)*x^2       if |x| ≤ 1
         (1/6)*(2 - |x|)^2           if |x| ≤ 2
         0                           if |x| ≥ 2
```

The expression `ker'` yields a kernel instance which is the 1st derivative of the cubic spline `ker` (also see the constructor [`CubicSplinePrime`](@ref)).
