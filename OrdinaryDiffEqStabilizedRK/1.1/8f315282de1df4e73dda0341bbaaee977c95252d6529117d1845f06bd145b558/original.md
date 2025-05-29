```
ESERK5(; eigen_est = nothing)
```

J. Martín-Vaquero, A. Kleefeld. ESERK5: A fifth-order extrapolated stabilized explicit Runge-Kutta method, Journal of Computational and Applied Mathematics, 356, pp 22-36, 2019. doi: https://doi.org/10.1016/j.cam.2019.01.040.

ESERK5: Stabilized Explicit Method. Fifth order extrapolated stabilized Runge-Kutta method. Exhibits high stability for real eigenvalues and is smoothened to allow for moderate sized complex eigenvalues.

This method takes the keyword argument `eigen_est` of the form

`eigen_est = (integrator) -> integrator.eigen_est = upper_bound`,

where `upper_bound` is an estimated upper bound on the spectral radius of the Jacobian matrix. If `eigen_est` is not provided, `upper_bound` will be estimated using the power iteration.
