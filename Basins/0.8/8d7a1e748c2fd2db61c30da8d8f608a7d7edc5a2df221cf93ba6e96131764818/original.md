```
draw_basin!(xg, yg, integ, iter_f!::Function, reinit_f!::Function)
```

Compute an estimate of the basin of attraction on a two-dimensional plane. This is a low level function, for higher level functions see: `basin_poincare_map`, `basin_discrete_map`, `basin_stroboscopic_map`

## Arguments

  * `xg`, `yg` : 1-dim range vector that defines the grid of the initial conditions to test.
  * `integ` : integrator handle of the dynamical system.
  * `iter_f!` : function that iterates the map or the system, see step! from DifferentialEquations.jl and

examples for a Poincaré map of a continuous system.

  * `reinit_f!` : function that sets the initial condition to test on a two dimensional projection of the phase space.
