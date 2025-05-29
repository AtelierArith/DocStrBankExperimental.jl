```
BSpline(degree)
```

B-spline kernel. `degree` is one of `Linear()`, `Quadratic()` or `Cubic()`.

!!! warning
    `BSpline(Quadratic())` and `BSpline(Cubic())` cannot handle boundaries correctly because the kernel values are merely truncated, which leads to unstable behavior. Therefore, it is recommended to use either `SteffenBSpline` or `KernelCorrection` in cases where proper handling of boundaries is necessary.

