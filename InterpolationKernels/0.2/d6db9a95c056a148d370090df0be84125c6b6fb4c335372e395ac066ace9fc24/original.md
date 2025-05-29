```
CardinalCubicSpline{T}(a)
```

yields an instance of the Keys family of cardinal cubic splines for floating-point type `T` and parameter `a = ker'(1)` the slope of the function `ker(x)` at `x = 1`.

These kernels are C¹ continuous piecewise normalized cardinal cubic spline which depend on one parameter `a` and defined by:

```
ker(x) = 1 + ((2 + a)*|x| - (3 + a))*x^2    if |x| ≤ 1
         a*(|x| - 1)*(|x| - 2)^2            if 1 ≤ |x| ≤ 2
         0                                  if |x| ≥ 2
```

The expression `ker'` yields a kernel instance which is the 1st derivative of the Keys kernel `ker` (also see the constructor [`CardinalCubicSplinePrime`](@ref)).

Reference:

  * Keys, Robert, G., "*Cubic Convolution Interpolation for Digital Image Processing*", IEEE Trans. Acoustics, Speech, and Signal Processing, Vol. ASSP-29, No. 6, December 1981, pp. 1153-1160.
