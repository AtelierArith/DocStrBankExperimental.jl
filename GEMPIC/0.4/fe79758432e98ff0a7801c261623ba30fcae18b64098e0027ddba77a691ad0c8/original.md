```
HamiltonianSplitting( maxwell_solver,
                      kernel_smoother_0, kernel_smoother_1,
                      particle_group, e_dofs, b_dofs)
```

Hamiltonian splitting type for Vlasov-Maxwell

  * Integral over the spline function on each interval (order p+1)
  * Integral over the spline function on each interval (order p)
  * `e_dofs` describing the two components of the electric field
  * `b_dofs` describing the magnetic field
  * `j_dofs` for kernel representation of current density.
