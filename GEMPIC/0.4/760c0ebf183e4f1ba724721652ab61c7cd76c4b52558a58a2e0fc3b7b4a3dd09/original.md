solve*poisson!( efield, particle*group, kernel*smoother, maxwell*solver, rho )

Accumulate rho and solve Poisson

  * `particle_group` : Particles
  * `maxwell_solver` : Maxwell solver (FEM 1D)
  * `kernel_smoother_0` : Particle-Mesh method
  * `rho` : preallocated array for Charge density
  * `efield_dofs` : spline coefficients of electric field (1D)
