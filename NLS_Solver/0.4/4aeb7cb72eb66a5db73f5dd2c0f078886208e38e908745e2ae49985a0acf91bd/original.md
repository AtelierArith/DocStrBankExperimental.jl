```julia
abstract type Abstract_Solver_Conf end
```

Abstract solver configuration. These are the solvers to be used to solve unconstrained nonlinear least squares:

$$
\min\limits_\theta \frac{1}{2}\|r(\theta)\|^2
$$

Implementations:

  * [`LevenbergMarquardt_Conf`](@ref)
