```
sysd, x0map = c2d_x0map(sys::AbstractStateSpace{<:Continuous}, Ts, method=:zoh; w_prewarp=0)
```

Returns the discretization `sysd` of the system `sys` and a matrix `x0map` that transforms the initial conditions to the discrete domain by `x0_discrete = x0map*[x0; u0]`

See `c2d` for further details.
