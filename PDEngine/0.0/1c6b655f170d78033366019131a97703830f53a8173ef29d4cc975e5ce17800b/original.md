Solve the 2D Navier-Stokes equations using the finite difference method. The Navier-Stokes equations describe the motion of viscous fluid substances.

Arguments:

  * N: Number of grid points in each direction (excluding boundary points)
  * ν: Kinematic viscosity
  * T: Total simulation time
  * Δx: Spatial step size
  * Δt: Temporal step size

Returns:

  * u: x-component of velocity field
  * v: y-component of velocity field
  * p: Pressure field
