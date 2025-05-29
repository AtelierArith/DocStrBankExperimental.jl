```julia
abstract type Abstract_BC_Solver_Conf end
```

Abstract solver configuration. These are the solvers to be used to solve bound constrained nonlinear least squares:

$$
\min\limits_{\theta_l \le \theta \le \theta_u } \frac{1}{2}\|r(\theta)\|^2
$$

Implementations:

  * [`LevenbergMarquardt_BC_Conf`](@ref)
