Assyr Abdulle, Alexei A. Medovikov. Second Order Chebyshev Methods based on Orthogonal Polynomials. Numerische Mathematik, 90 (1), pp 1-18, 2001. doi: https://dx.doi.org/10.1007/s002110100292

ROCK2: Stabilized Explicit Method. Second order stabilized Runge-Kutta method. Exhibits high stability for real eigenvalues and is smoothened to allow for moderate sized complex eigenvalues.

This method takes optional keyword arguments `min_stages`, `max_stages`, and `eigen_est`. The function `eigen_est` should be of the form

`eigen_est = (integrator) -> integrator.eigen_est = upper_bound`,

where `upper_bound` is an estimated upper bound on the spectral radius of the Jacobian matrix. If `eigen_est` is not provided, `upper_bound` will be estimated using the power iteration.
