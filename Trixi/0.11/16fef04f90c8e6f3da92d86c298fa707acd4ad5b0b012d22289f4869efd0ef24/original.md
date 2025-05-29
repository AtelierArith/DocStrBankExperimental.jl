```
min_max_speed_naive(u_ll, u_rr, orientation::Integer, equations)
min_max_speed_naive(u_ll, u_rr, normal_direction::AbstractVector, equations)
```

Simple and fast estimate(!) of the minimal and maximal wave speed of the Riemann problem with left and right states `u_ll, u_rr`, usually based only on the local wave speeds associated to `u_ll` and `u_rr`. Slightly more diffusive than [`min_max_speed_davis`](@ref).

  * Amiram Harten, Peter D. Lax, Bram van Leer (1983) On Upstream Differencing and Godunov-Type Schemes for Hyperbolic Conservation Laws [DOI: 10.1137/1025002](https://doi.org/10.1137/1025002)

See eq. (10.37) from

  * Eleuterio F. Toro (2009) Riemann Solvers and Numerical Methods for Fluid Dynamics: A Practical Introduction [DOI: 10.1007/b79761](https://doi.org/10.1007/b79761)

See also [`FluxHLL`](@ref), [`min_max_speed_davis`](@ref), [`min_max_speed_einfeldt`](@ref).
