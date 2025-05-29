```
cauchy_integral(f [; a = 0, n  = 1, radius = 1])
```

Evaluate the integral of `n!/(2πi) f(z)/(z-a)^n` along a circular contour with radius `radius` around the point `a`.

If the integrand is analytic inside the contour except at the pole around `z=a` then its value should correspond to the derivative `f^(n)(a)`.
