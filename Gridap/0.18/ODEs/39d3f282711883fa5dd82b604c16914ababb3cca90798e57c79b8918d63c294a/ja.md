```
struct ThetaMethod <: ODESolver end
```

θ法 ODE ソルバー。

```
residual(tx, ux, vx) = 0,

tx = t_n + θ * dt
ux = u_n + θ * dt * x
vx = x,

u_(n+1) = u_n + dt * x.
```
