```
ksmin_adaptive(x, hardness=50; tol=1e-6, smoothing_fraction=0.1)
```

Kreisselmeier–Steinhauser constraint aggregation function using the adaptive hardness proposed by Poon and Martins in "An adaptive approach to constraint aggregation using adjoint sensitivity analysis".  This implementation uses Newton's method rather than the secant method for increasing hardness values. Some blending is also used to ensure that result is C1 continuous. `smoothing_fraction` controls the smoothness of this blending.
