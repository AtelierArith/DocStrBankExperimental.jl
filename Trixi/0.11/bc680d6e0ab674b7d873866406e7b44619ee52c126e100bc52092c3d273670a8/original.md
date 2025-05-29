```
flux_shima_etal_turbo(u_ll, u_rr, orientation_or_normal_direction, equations)
```

Equivalent to [`flux_shima_etal`](@ref) except that it may use specialized methods, e.g., when used with [`VolumeIntegralFluxDifferencing`](@ref). These specialized methods may enable better use of SIMD instructions to increase runtime efficiency on modern hardware.
