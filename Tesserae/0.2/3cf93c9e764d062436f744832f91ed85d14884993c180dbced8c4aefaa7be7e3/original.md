```
KernelCorrection(kernel)
```

`KernelCorrection`[^KC] modifies `kernel` to achieve stable simulations near boundaries. The corrected kernel satisfies not only the partition of unity, $\sum_i w_{ip} = 1$, but also the linear field reproduction, $\sum_i w_{ip} \bm{x}_i = \bm{x}_p$, near boundaries. In the implementation, this simply applies [`WLS`](@ref) near boundaries. `kernel` is one of [`BSpline`](@ref) and [`uGIMP`](@ref). See also [`SteffenBSpline`](@ref).

[^KC]: [Nakamura, K., Matsumura, S., & Mizutani, T. (2023). Taylor particle-in-cell transfer and kernel correction for material point method. *Computer Methods in Applied Mechanics and Engineering*, 403, 115720.](https://doi.org/10.1016/j.cma.2022.115720)
