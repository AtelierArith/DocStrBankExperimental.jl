```
RKC(; eigen_est = nothing)
```

B. P. Sommeijer, L. F. Shampine, J. G. Verwer. RKC: An Explicit Solver for Parabolic PDEs, Journal of Computational and Applied Mathematics, 88(2), pp 315-326, 1998. doi: https://doi.org/10.1016/S0377-0427(97)00219-7

RKC: Stabilized Explicit Method. Second order stabilized Runge-Kutta method. Exhibits high stability for real eigenvalues.

This method takes the keyword argument `eigen_est` of the form

`eigen_est = (integrator) -> integrator.eigen_est = upper_bound`,

where `upper_bound` is an estimated upper bound on the spectral radius of the Jacobian matrix. If `eigen_est` is not provided, `upper_bound` will be estimated using the power iteration.
