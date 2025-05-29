```julia
l94_stencil(ϕ, U, Δt, Δz; kwargs...)

```

L94 advection in 1-D (Lin et al., 1994)

  * ϕ is the scalar field at the current time step, it should be a vector of length 5.
  * U is the velocity at both edges of the central grid cell, it should be a vector of length 2.
  * Δt is the length of the time step.
  * Δz is the grid spacing.

The output will be time derivative of the central index (i.e. index 3) of the ϕ vector (i.e. dϕ/dt).

(The output is dependent on the Courant number, which depends on Δt, so Δt needs to be an input to the function.)
