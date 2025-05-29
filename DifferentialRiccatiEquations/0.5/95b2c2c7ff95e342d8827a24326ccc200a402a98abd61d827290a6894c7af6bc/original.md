```
Newton(inner_alg; kwargs...)
Newton(; kwargs...)
```

Kleinman-Newton method to solve algebraic Riccati equations.

```
solve(prob::GAREProblem, Newton(; kwargs...); solve_kwargs...)
```

Supported keyword arguments:

  * `inner_alg = ADI()`: algorithm to solve inner Lyapunov equations arizing at every Newton step
  * `maxiters = 5`: maximum number of Newton steps
  * `reltol = nothing`: relative tolerance of Riccati residual; if set to `nothing`, equivalent to `size(prob.A, 1) * eps()`
  * `abstol = nothing`: absolute tolerance of Riccati residual; if set to `nothing`, equivalent to `reltol * norm(prob.Q)` (residual of zero value)
  * `observer`: see [`Callbacks`](@ref)
  * `inexact = true`: whether to allow (more) inexact Lyapunov solutions
  * `inexact_forcing = quadratic_forcing`: compute the forcing parameter `η = inexact_forcing(i, residual_norm)` as described by Dembo et al. (1982), where `i::Int` is the Newton step and `residual_norm::Float64` is the norm of the Riccati residual. See [`quadratic_forcing`](@ref), and [`superlinear_forcing`](@ref).
  * `inexact_hybrid = true`: whether to switch to the classical Newton method, if the absolute Lyapunov tolerance of the classical Newton method is less strict (i.e. larger) than the tolerance `η * residual_norm`.
  * `linesearch = true`: whether to perform an Armijo line search if the Riccati residual did not decrease sufficiently, see e.g. Benner et al. (2015).

References:

  * Dembo, Eisenstat, Steihaug: Inexact Newton Methods. 1982. https://doi.org/10.1137/0719025
  * Benner, Heinkenschloss, Saak, Weichelt: Inexact low-rank Newton-ADI method for large-scale algebraic Riccati equations. 2015. http://www.mpi-magdeburg.mpg.de/preprints/
