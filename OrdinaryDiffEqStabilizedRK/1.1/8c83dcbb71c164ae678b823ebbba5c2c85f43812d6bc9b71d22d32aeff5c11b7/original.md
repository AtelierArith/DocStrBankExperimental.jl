```
ROCK4(; min_stages = 0, max_stages = 152, eigen_est = nothing)
```

Assyr Abdulle. Fourth Order Chebyshev Methods With Recurrence Relation. 2002 Society for Industrial and Applied Mathematics Journal on Scientific Computing, 23(6), pp 2041-2054, 2001. doi: https://doi.org/10.1137/S1064827500379549

ROCK4: Stabilized Explicit Method. Fourth order stabilized Runge-Kutta method. Exhibits high stability for real eigenvalues and is smoothened to allow for moderate sized complex eigenvalues.

This method takes optional keyword arguments `min_stages`, `max_stages`, and `eigen_est`. The function `eigen_est` should be of the form

`eigen_est = (integrator) -> integrator.eigen_est = upper_bound`,

where `upper_bound` is an estimated upper bound on the spectral radius of the Jacobian matrix. If `eigen_est` is not provided, `upper_bound` will be estimated using the power iteration.
