```
LinearSpline([T=Float64,] B=Flat)
```

yields an instance of the linear spline for floating-point type `T` and boundary conditions `B`.

The linear spline (also known as *triangle kernel*, as *Bartlett window* or as *Fejér window*) is the 2nd order (linear) B-spline given by:

```
ker(x) = 1 - |x|       if |x| ≤ 1
         0             if |x| ≥ 1
```

The expression `ker'` yields a kernel instance which is the 1st derivative of the linear spline `ker` (also see the constructor [`LinearSplinePrime`](@ref)).
