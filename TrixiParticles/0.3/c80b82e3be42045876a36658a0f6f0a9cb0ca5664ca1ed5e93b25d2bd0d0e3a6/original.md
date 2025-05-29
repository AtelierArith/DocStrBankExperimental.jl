```
KernelCorrection()
```

Kernel correction, as explained by [Bonet (1999)](@cite Bonet1999), uses Shepard interpolation to obtain a 0-th order accurate result, which was first proposed by Li et al. This can be further extended to obtain a kernel corrected gradient as shown by [Basa et al. (2008)](@cite Basa2008).

The kernel correction coefficient is determined by

$$
c(x) = \sum_{b=1} V_b W_b(x)
$$

The gradient of corrected kernel is determined by

$$
\nabla \tilde{W}_{b}(r) =\frac{\nabla W_{b}(r) - W_b(r) \gamma(r)}{\sum_{b=1} V_b W_b(r)} , \quad  \text{where} \quad
\gamma(r) = \frac{\sum_{b=1} V_b \nabla W_b(r)}{\sum_{b=1} V_b W_b(r)}.
$$

This correction can be applied with [`SummationDensity`](@ref) and [`ContinuityDensity`](@ref), which leads to an improvement, especially at free surfaces.

!!! note
      * This only works when the boundary model uses [`SummationDensity`](@ref) (yet).
      * It is also referred to as "0th order correction".
      * In 2D, we can expect an increase of about 10–15% in computation time.

