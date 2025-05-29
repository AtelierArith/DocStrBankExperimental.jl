```
TerminateSteadyState(abstol = 1e-8, reltol = 1e-6, test = allDerivPass; min_t = nothing,
    wrap_test::Val = Val(true))
```

`TerminateSteadyState` can be used to solve the problem for the steady-state by running the solver until the derivatives of the problem converge to 0 or `tspan[2]` is reached. This is an alternative approach to root finding (see the [Steady State Solvers](https://docs.sciml.ai/DiffEqDocs/stable/solvers/steady_state_solve/) section).

## Arguments

  * `abstol` and `reltol` are the absolute and relative tolerance, respectively. These tolerances may be specified as scalars or as arrays of the same length as the states of the problem.
  * `test` represents the function that evaluates the condition for termination. The default condition is that all derivatives should become smaller than `abstol` or the states times `reltol`. The user can pass any other function to implement a different termination condition. Such function should take four arguments: `integrator`, `abstol`, `reltol`, and `min_t`.
  * `wrap_test` can be set to `Val(false)`, in which case `test` must have the definition `test(u, t, integrator)`. Otherwise, `test` must have the definition `test(integrator, abstol, reltol, min_t)`.

## Keyword Arguments

  * `min_t` specifies an optional minimum `t` before the steady state calculations are allowed to terminate.
