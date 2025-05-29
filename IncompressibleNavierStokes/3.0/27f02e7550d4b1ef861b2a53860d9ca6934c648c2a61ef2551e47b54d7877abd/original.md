```julia
velocityfield(setup, ufunc; ...) -> Any
velocityfield(setup, ufunc, t; psolver, doproject) -> Any

```

Create divergence free velocity field `u` with boundary conditions at time `t`. The initial conditions of `u[α]` are specified by the function `ufunc(α, x...)`.
