```julia
upwind2_stencil(ϕ, U, Δt, Δz; kwargs...)

```

Second-order upwind advection in 1-D, otherwise known as linear-upwind differencing (LUD): https://en.wikipedia.org/wiki/Upwind_scheme.

  * ϕ is the scalar field at the current time step, it should be a vector of length 5 (2 cells on the left, the central cell, and 2 cells on the right).
  * U is the velocity at both edges of the central grid cell, it should be a vector of length 2.
  * Δt is the length of the time step.
  * Δz is the grid spacing.

The output will be time derivative of the central index (i.e. index 3) of the ϕ vector (i.e. dϕ/dt).

(Δt is not used, but is a function argument for consistency with other operators.)
