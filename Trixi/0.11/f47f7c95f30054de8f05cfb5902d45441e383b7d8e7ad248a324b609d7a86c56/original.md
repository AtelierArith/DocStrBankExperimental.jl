```
VolumeIntegralSubcellLimiting(limiter;
                              volume_flux_dg, volume_flux_fv)
```

A subcell limiting volume integral type for DG methods based on subcell blending approaches with a low-order FV method. Used with limiter [`SubcellLimiterIDP`](@ref).

!!! note
    Subcell limiting methods are not fully functional on non-conforming meshes. This is mainly because the implementation assumes that low- and high-order schemes have the same surface terms, which is not guaranteed for non-conforming meshes. The low-order scheme with a high-order mortar is not invariant domain preserving.

