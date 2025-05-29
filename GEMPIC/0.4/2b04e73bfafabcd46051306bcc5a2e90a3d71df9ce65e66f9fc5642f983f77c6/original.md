```
maxwell_solver = MaxwellFEM1D( mesh, degree )
```

1D Maxwell spline finite element solver on a periodic grid

  * `Lx`                   : length of Periodic domain
  * `delta_x`              : cell size
  * `n_dofs`               : number of cells (and grid points)
  * `s_deg_0`              : spline degree 0-forms
  * `s_deg_1`              : spline degree 1-forms
  * `mass_0`               : coefficients of 0-form mass matrix
  * `mass_1`               : coefficients of 1-form mass matrix
  * `eig_mass0`            : eigenvalues of circulant 0-form mass matrix
  * `eig_mass1`            : eigenvalues of circulant 1-form mass matrix
  * `eig_weak_ampere`      : eigenvalues of circulant update matrix for Ampere
  * `eig_weak_poisson`     : eigenvalues of circulant update matrix for Poisson
  * `plan_fw`              : fft plan (forward)
  * `plan_bw`              : fft plan (backward)
