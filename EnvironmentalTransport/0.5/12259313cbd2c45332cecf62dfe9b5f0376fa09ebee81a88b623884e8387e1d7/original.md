```julia
upwind1_stencil(ϕ, U, Δt, Δz; p)

```

First-order upwind advection in 1-D: https://en.wikipedia.org/wiki/Upwind_scheme.

  * ϕ is the scalar field at the current time step, it should be a vector of length 3 (1 cell on the left, the central cell, and 1 cell on the right).
  * U is the velocity at both edges of the central grid cell, it should be a vector of length 2.
  * Δt is the length of the time step.
  * Δz is the grid spacing.

The output will be time derivative of the central index (i.e. index 2) of the ϕ vector (i.e. dϕ/dt).

`Δt` and `p` are not used, but are function arguments for consistency with other operators.
