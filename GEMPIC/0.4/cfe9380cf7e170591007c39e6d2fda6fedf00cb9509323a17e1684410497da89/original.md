```
HamiltonianSplittingBoris( maxwell_solver,
                           kernel_smoother_0, kernel_smoother_1,
                           particle_group,
                           e_dofs_1, e_dofs_2, b_dofs)
```

Boris pusher in GEMPIC framework (spline finite elements)

  * `mid` describing the magnetic field at time $t_{n+1/2}$ (used for push)
  * `j_dofs` for kernel representation of current density.
  * `maxwell_solver`    : Maxwell solver
  * `kernel_smoother_0` : Kernel smoother
  * `kernel_smoother_1` : Kernel smoother
  * `particle_group`    : Particle group
  * `efield_dofs`       : array for the coefficients of the efields
  * `bfield_dofs`       : array for the coefficients of the bfield
  * `x_min`             : Lower bound of x domain
  * `Lx`                : Length of the domain in x direction.
