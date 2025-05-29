```
FluxHLL(min_max_speed=min_max_speed_davis)
```

Create an HLL (Harten, Lax, van Leer) numerical flux where the minimum and maximum wave speeds are estimated as `λ_min, λ_max = min_max_speed(u_ll, u_rr, orientation_or_normal_direction, equations)`, defaulting to [`min_max_speed_davis`](@ref). Original paper:

  * Amiram Harten, Peter D. Lax, Bram van Leer (1983) On Upstream Differencing and Godunov-Type Schemes for Hyperbolic Conservation Laws [DOI: 10.1137/1025002](https://doi.org/10.1137/1025002)
