```
write_step!( thdiag, time, degree, efield_dofs, bfield_dofs,
             efield_dofs_n, efield_poisson)
```

write diagnostics for PIC

  * `time` : Time
  * `efield_dofs` : Electric field
  * `efield_dofs_n` : Electric field at half step
  * `efield_poisson` : Electric field compute from Poisson equation
  * `bfield_dofs` : Magnetic field
  * `degree` : Spline degree
