```julia
coarse_grain_timescale(bath, lim; rtol, atol)

```

Calculate the optimal coarse grain time scale $T_a=√{τ_{SB}τ_B/5}$ for a total evolution time `lim`. `atol` and `rtol` are the absolute and relative error for the integration.
