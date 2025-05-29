```
GeneralDomain(
    g, u = nothing; save = true, abstol = nothing, scalefactor = nothing,
    autonomous = nothing, domain_jacobian = nothing,
    nlsolve_kwargs = (; abstol = 10 * eps()), kwargs...)
```

A `GeneralDomain` callback in DiffEqCallbacks.jl generalizes the concept of a `PositiveDomain` callback to arbitrary domains.

Domains are specified by

  * in-place functions `g(resid, u, p)` or `g(resid, u, p, t)` if the corresponding ODEProblem is an inplace problem, or
  * out-of-place functions `g(u, p)` or `g(u, p, t)` if the corresponding ODEProblem is an out-of-place problem.

The function calculates residuals of a state vector `u` at time `t` relative to that domain, with `p` the parameters of the corresponding integrator.

As for `PositiveDomain`, steps are accepted if residuals of the extrapolated values at the next time step are below a certain tolerance. Moreover, this callback is automatically coupled with a `ManifoldProjection` that keeps all calculated state vectors close to the desired domain, but in contrast to a `PositiveDomain` callback the nonlinear solver in a `ManifoldProjection` cannot guarantee that all state vectors of the solution are actually inside the domain. Thus, a `PositiveDomain` callback should generally be preferred.

## Arguments

  * `g`: the implicit definition of the domain as a function as described above which is zero when the value is in the domain.
  * `u`: A prototype of the state vector of the integrator. A copy of it is saved and extrapolated values are written to it. If it is not specified, every application of the callback allocates a new copy of the state vector.

## Keyword Arguments

  * `save`: Whether to do the standard saving (applied after the callback).
  * `abstol`: Tolerance up to, which residuals are accepted. Element-wise tolerances are allowed. If it is not specified, every application of the callback uses the current absolute tolerances of the integrator.
  * `scalefactor`: Factor by which an unaccepted time step is reduced. If it is not specified, time steps are halved.
  * `autonomous`: Whether `g` is an autonomous function of the form `g(resid, u, p)`. If it is not specified, it is determined automatically.
  * `kwargs`: All other keyword arguments are passed to [`ManifoldProjection`](@ref).
  * `nlsolve_kwargs`: All keyword arguments are passed to the nonlinear solver in `ManifoldProjection`. The default is `(; abstol = 10 * eps())`.
  * `domain_jacobian`: The Jacobian of the domain (wrt the state). This has the same signature as `g` and the first argument is the Jacobian if inplace. This corresponds to the `manifold_jacobian` argument of [`ManifoldProjection`](@ref). Note that passing a `manifold_jacobian` is not supported for `GeneralDomain` and results in an error.

## References

Shampine, Lawrence F., Skip Thompson, Jacek Kierzenka and G. D. Byrne. Non-negative solutions of ODEs. Applied Mathematics and Computation 170 (2005): 556-569.
