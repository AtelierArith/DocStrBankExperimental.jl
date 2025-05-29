```
equal_angle_intervals(ntheta, nphi)
```

Discretize the sky into `ntheta` zenith rings of `nphi` sectors each assuming the same angle intervals for each sector (Δθ = π/2/ntheta and ΔΦ = 2π/nphi). Returns an object of type `SkySectors`. See package documentation for details.
