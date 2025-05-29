```
RectangularSpline([T=Float64,] B=Flat)
```

yields an instance of the rectangular spline for floating-point type `T` and boundary conditions `B`.

The rectangular spline (also known as *box kernel*, as *Fourier window* or as *Dirichlet window*) is the 1st order (constant) B-spline equals to `1` on `[-1/2,+1/2)`, and `0` elsewhere.

The expression `ker'` yields a kernel instance which is the 1st derivative of the rectangular spline `ker` (also see the constructor [`RectangularSplinePrime`](@ref)).
