```
struct ForwardEuler <: ODESolver end
```

フォワードオイラーODEソルバー。

```
residual(tx, ux, vx) = 0,

tx = t_n
ux = u_n
vx = x,

u_(n+1) = u_n + dt * x.
```
