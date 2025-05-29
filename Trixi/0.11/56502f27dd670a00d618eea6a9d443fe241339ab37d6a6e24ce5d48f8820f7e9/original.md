```
flux_godunov(u_ll, u_rr, orientation, 
             equations::LinearScalarAdvectionEquation1D)
```

Godunov (upwind) flux for the 1D linear scalar advection equation. Essentially first order upwind, see e.g. https://math.stackexchange.com/a/4355076/805029 .
