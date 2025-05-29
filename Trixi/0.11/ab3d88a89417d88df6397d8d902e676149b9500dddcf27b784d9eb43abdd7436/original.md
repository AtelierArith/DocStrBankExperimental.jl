```
min_max_speed_davis(u_ll, u_rr, orientation::Integer, equations)
min_max_speed_davis(u_ll, u_rr, normal_direction::AbstractVector, equations)
```

Simple and fast estimates of the minimal and maximal wave speed of the Riemann problem with left and right states `u_ll, u_rr`, usually based only on the local wave speeds associated to `u_ll` and `u_rr`.

  * S.F. Davis (1988) Simplified Second-Order Godunov-Type Methods [DOI: 10.1137/0909030](https://doi.org/10.1137/0909030)

See eq. (10.38) from

  * Eleuterio F. Toro (2009) Riemann Solvers and Numerical Methods for Fluid Dynamics: A Practical Introduction [DOI: 10.1007/b79761](https://doi.org/10.1007/b79761)

See also [`FluxHLL`](@ref), [`min_max_speed_naive`](@ref), [`min_max_speed_einfeldt`](@ref).
