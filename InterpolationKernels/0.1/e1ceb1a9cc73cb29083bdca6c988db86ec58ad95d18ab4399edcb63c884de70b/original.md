```
KeysSpline([T=Float64,] a, B=Flat)
```

yields an instance of the Keys family of cardinal kernels for floating-point type `T`, parameter `a` and boundary conditions `B`.

These kernels are piecewise normalized cardinal cubic spline which depend on one parameter `a` which is the slope of the spline at abscissa 1.  Keys cardinal kernels are defined by:

```
ker(x) = p(abs(x))   if abs(x) ≤ 1
         q(abs(x))   if 1 ≤ abs(x) ≤ 2
         0           if abs(x) ≥ 2
```

with:

```
p(x) = 1 - (a + 3)*x^2 + (a + 2)*x^3
q(x) = -4a + 8a*x - 5a*x^2 + a*x^3
```

The expression `ker'` yields a kernel instance which is the 1st derivative of the Keys kernel `ker` (also see the constructor [`KeysSplinePrime`](@ref)).

Reference:

  * Keys, Robert, G., "Cubic Convolution Interpolation for Digital Image Processing", IEEE Trans. Acoustics, Speech, and Signal Processing, Vol. ASSP-29, No. 6, December 1981, pp. 1153-1160.
