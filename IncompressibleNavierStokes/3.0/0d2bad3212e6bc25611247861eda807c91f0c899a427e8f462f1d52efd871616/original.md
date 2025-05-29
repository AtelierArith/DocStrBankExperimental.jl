```julia
poisson(psolver, f) -> Any

```

Solve the Poisson equation for the pressure with right hand side `f` at time `t`. For periodic and no-slip BC, the sum of `f` should be zero.

Differentiable version.
