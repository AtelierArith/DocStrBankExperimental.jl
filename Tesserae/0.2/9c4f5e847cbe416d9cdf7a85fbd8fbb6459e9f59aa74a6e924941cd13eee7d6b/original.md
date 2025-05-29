```
SteffenBSpline(degree)
```

B-spline kernel with boundary correction by Steffen et al.[^Steffen] `SteffenBSpline` satisfies the partition of unity, $\sum_i w_{ip} = 1$, near boundaries. See also [`KernelCorrection`](@ref).

[^Steffen]: [Steffen, M., Kirby, R. M., & Berzins, M. (2008). Analysis and reduction of quadrature errors in the material point method (MPM). *International journal for numerical methods in engineering*, 76(6), 922-948.](https://doi.org/10.1002/nme.2360)
