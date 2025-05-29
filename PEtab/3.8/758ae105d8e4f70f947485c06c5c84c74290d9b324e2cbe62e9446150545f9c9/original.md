```
SteadyStateSolver(method::Symbol; kwargs...)
```

Steady-state solver options (`method`, `tolerances`, etc.) for computing the steady state, where the ODE right-hand side `f` fulfills `du = f(u, p, t) ≈ 0`.

The steady state can be computed in two ways. If `method=:Simulate`, by simulating the ODE model until `du = f(u, p, t) ≈ 0` using ODE solver options defined in the provied `ODESolver` to the `PEtabODEProblem. This approach is **strongly** recommended. If`method=:Rootfinding`, by directly finding the root of the RHS`f(u, p, t) = 0` using any algorithm from NonlinearSolve.jl. The root-finding approach is far less reliable than the simulation approach (see description below).

## Keyword Arguments

  * `termination_check = :wrms`: Approach to check if the model has reached steady-state for   `method = :Simulate`. Two approaches are supported:

      * `:wrms`: Weighted root-mean-square. Terminate when: $\sqrt{\frac{1}{N} \sum_i^N \Big( \frac{du_i}{reltol * u_i + abstol}\Big)^2} < 1$
      * `:Newton`: Terminate if the step for Newton's method `Δu` is sufficiently small: $\sqrt{\frac{1}{N} \sum_i^N \Big(\frac{\Delta u_i}{reltol * u_i + abstol}\Big)^2} < 1$ The `:Newton` approach requires that the Newton step `Δu` can be computed, which is only possible if the Jacobian of the RHS of the ODE model is invertible. If this is not the case, a pseudo-inverse is used if `pseudoinverse = true`, else `wrms` is used. The `:Newton` termination should perform better than `:wrms` as it accounts for the scale of the ODEs, but until benchmarks confirm this, we recommend `:wrms`.
  * `pseudoinverse = true`: Whether to use a pseudo-inverse if inverting the Jacobian fails   for `termination_check = :Newton`.
  * `rootfinding_alg = nothing`: Root-finding algorithm from NonlinearSolve.jl to use if   `method = :Rootfinding`. If left empty, the default NonlinearSolve.jl algorithm is used.
  * `abstol`: Absolute tolerance for the NonlinearSolve.jl root-finding problem or the   `termination_check` formula. Defaults to `100 * abstol_ode`, where `abstol_ode` is the   tolerance for the `ODESolver` in the `PEtabODEProblem`.
  * `reltol`: Relative tolerance for the NonlinearSolve.jl root-finding problem or the   `termination_check` formula. Defaults to `100 * reltol_ode`, where `reltol_ode` is the   tolerance for the `ODESolver` in the `PEtabODEProblem`.
  * `maxiters`: Maximum number of iterations to use if `method = :Rootfinding`.

## Description

For an ODE model of the form:

$$
\frac{\mathrm{d}u}{\mathrm{d}t} = du = f(u, p, t)
$$

The steady state is defined by:

$$
f(u, p, t) = 0.0
$$

The steady state can be computed in two ways: either by simulating the ODE model from a set of initial values `u₀` until `du ≈ 0`, or by using a root-finding algorithm such as [Newton's method](https://en.wikipedia.org/wiki/Newton%27s_method) to directly solve `f(u, p, t) = 0.0`. While the root-finding approach is computationally more efficient (since it does not require solving the entire ODE), it is far less reliable and can converge to the wrong root. For example, in mass-action models with positive initial values, the feasible root should be positive in `u`. This is generally fulfilled when computing the steady state via simulation (a negative root typically only occurs if the ODE solver fails). However, with root-finding, there is no such guarantee, as any root that satisfies `f(u, p, t) = 0.0` may be returned. Consistent with this, benchmarks have shown that simulation is the most reliable method [1].

Another alternative is to solve for the steady state  symbolically. If feasible, this is the most computationally efficient approach [1].

1. Fiedler et al, BMC system biology, pp 1-19 (2016)
