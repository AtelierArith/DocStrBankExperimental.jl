```
flux_godunov(u_ll, u_rr, orientation_or_normal_direction, 
             equations::LinearScalarAdvectionEquation2D)
```

Godunov (upwind) flux for the 2D linear scalar advection equation. Essentially first order upwind, see e.g. https://math.stackexchange.com/a/4355076/805029 .
