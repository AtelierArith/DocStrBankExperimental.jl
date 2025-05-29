```
ESERK4(; eigen_est = nothing)
```

J. Martín-Vaquero, B. Kleefeld. Extrapolated stabilized explicit Runge-Kutta methods, Journal of Computational Physics, 326, pp 141-155, 2016. doi: https://doi.org/10.1016/j.jcp.2016.08.042.

ESERK4: Stabilized Explicit Method. Fourth order extrapolated stabilized Runge-Kutta method. Exhibits high stability for real eigenvalues and is smoothened to allow for moderate sized complex eigenvalues.

This method takes the keyword argument `eigen_est` of the form

`eigen_est = (integrator) -> integrator.eigen_est = upper_bound`,

where `upper_bound` is an estimated upper bound on the spectral radius of the Jacobian matrix. If `eigen_est` is not provided, `upper_bound` will be estimated using the power iteration.
