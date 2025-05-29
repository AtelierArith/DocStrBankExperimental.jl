```
ShepardKernelCorrection()
```

Kernel correction, as explained by [Bonet (1999)](@cite Bonet1999), uses Shepard interpolation to obtain a 0-th order accurate result, which was first proposed by [Li et al. (1996)](@cite Li1996).

The kernel correction coefficient is determined by

$$
c(x) = \sum_{b=1} V_b W_b(x),
$$

where $V_b = m_b / \rho_b$ is the volume of particle $b$.

This correction is applied with [`SummationDensity`](@ref) to correct the density and leads to an improvement, especially at free surfaces.

!!! note
      * It is also referred to as "0th order correction".
      * In 2D, we can expect an increase of about 5–6% in computation time.

