Solve the 1D wave equation using the finite element method (FEM). The wave equation is given by: ∂²u/∂t² = c² ∇²u where c is the wave speed.

Arguments:

  * N: Number of spatial grid points (excluding boundary points)
  * c: Wave speed
  * T: Total simulation time
  * Δx: Spatial step size
  * Δt: Temporal step size

Returns:

  * u: The final displacement field
