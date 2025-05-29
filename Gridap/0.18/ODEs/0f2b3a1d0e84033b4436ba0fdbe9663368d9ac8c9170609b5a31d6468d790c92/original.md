```
struct GeneralizedAlpha1 <: ODESolver
```

Generalized-α first-order ODE solver.

```
residual(tx, ux, vx) = 0,

tx = (1 - αf) * t_n + αf * t_(n+1)
ux = (1 - αf) * u_n + αf * u_(n+1)
vx = (1 - αm) * v_n + αm * v_(n+1),

u_(n+1) = u_n + dt * ((1 - γ) * v_n + γ * x)
v_(n+1) = x.
```
