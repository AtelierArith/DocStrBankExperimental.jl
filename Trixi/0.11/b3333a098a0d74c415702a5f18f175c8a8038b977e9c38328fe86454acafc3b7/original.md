```
DissipationLocalLaxFriedrichs(max_abs_speed=max_abs_speed_naive)
```

Create a local Lax-Friedrichs dissipation operator where the maximum absolute wave speed is estimated as `max_abs_speed(u_ll, u_rr, orientation_or_normal_direction, equations)`, defaulting to [`max_abs_speed_naive`](@ref).
