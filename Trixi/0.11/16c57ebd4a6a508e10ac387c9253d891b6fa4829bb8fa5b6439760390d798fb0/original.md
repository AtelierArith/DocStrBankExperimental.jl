```
SubcellLimiterIDPCorrection()
```

Perform antidiffusive correction stage for the a posteriori IDP limiter [`SubcellLimiterIDP`](@ref) called with [`VolumeIntegralSubcellLimiting`](@ref).

!!! note
    This callback and the actual limiter [`SubcellLimiterIDP`](@ref) only work together. This is not a replacement but a necessary addition.


## References

  * Rueda-Ramírez, Pazner, Gassner (2022) Subcell Limiting Strategies for Discontinuous Galerkin Spectral Element Methods [DOI: 10.1016/j.compfluid.2022.105627](https://doi.org/10.1016/j.compfluid.2022.105627)
  * Pazner (2020) Sparse invariant domain preserving discontinuous Galerkin methods with subcell convex limiting [DOI: 10.1016/j.cma.2021.113876](https://doi.org/10.1016/j.cma.2021.113876)
