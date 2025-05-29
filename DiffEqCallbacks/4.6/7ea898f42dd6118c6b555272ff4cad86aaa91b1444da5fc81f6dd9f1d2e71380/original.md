```
ManifoldProjection(
    manifold; nlsolve = missing, save = true, autonomous = nothing,
    manifold_jacobian = nothing, autodiff = nothing, kwargs...)
```

In many cases, you may want to declare a manifold on which a solution lives. Mathematically, a manifold `M` is defined by a function `g` as the set of points where `g(u) = 0`. An embedded manifold can be a lower dimensional object which constrains the solution. For example, `g(u) = E(u) - C` where `E` is the energy of the system in state `u`, meaning that the energy must be constant (energy preservation). Thus by defining the manifold the solution should live on, you can retain desired properties of the solution.

`ManifoldProjection` projects the solution of the differential equation to the chosen manifold `g`, conserving a property while conserving the order. It is a consequence of convergence proofs both in the deterministic and stochastic cases that post-step projection to manifolds keep the same convergence rate, thus any algorithm can be easily extended to conserve properties. If the solution is supposed to live on a specific manifold or conserve such property, this guarantees the conservation law without modifying the convergence properties.

## Arguments

  * `manifold`: The residual function for the manifold. If the ODEProblem is an inplace problem, then `g` must be an inplace function of form `g(resid, u, p)` or `g(resid, u, p, t)` and similarly if the ODEProblem is an out-of-place problem then `g` must be a function of form `g(u, p)` or `g(u, p, t)`.

## Keyword Arguments

  * `nlsolve`: Defaults to a special single-factorize algorithm (denoted by `missing`) that would work in most cases (See [1] for details). Alternatively, a nonlinear solver as defined in the [NonlinearSolve.jl format](https://docs.sciml.ai/NonlinearSolve/stable/basics/solve/) can be specified. Additionally if NonlinearSolve.jl is loaded and `nothing` is specified a polyalgorithm is used.
  * `save`: Whether to do the standard saving (applied after the callback)
  * `autonomous`: Whether `g` is an autonomous function of the form `g(resid, u, p)` or `g(u, p)`. Specify it as `Val(::Bool)` to disable runtime branching. If `nothing`, we attempt to infer it from the signature of `g`.
  * `residual_prototype`: The size of the manifold residual. If it is not specified, we assume it to be same as `u` in the inplace case. Else we run a single evaluation of `manifold` to determine the size.
  * `kwargs`: All other keyword arguments are passed to [NonlinearSolve.jl](https://docs.sciml.ai/NonlinearSolve/stable/basics/solve/) if `nlsolve` is not `missing`.
  * `autodiff`: The autodifferentiation algorithm to use to compute the Jacobian if `manifold_jacobian` is not specified. This must be specified if `manifold_jacobian` is not specified.
  * `manifold_jacobian`: The Jacobian of the manifold (wrt the state). This has the same signature as `manifold` and the first argument is the Jacobian if inplace.

### Saveat Warning

Note that the `ManifoldProjection` callback modifies the endpoints of the integration intervals and thus breaks assumptions of internal interpolations. Because of this, the values for given by saveat will not be order-matching. However, the interpolation error can be proportional to the change by the projection, so if the projection is making small changes then one is still safe. However, if there are large changes from each projection, you should consider only saving at stopping/projection times. To do this, set `tstops` to the same values as `saveat`. There is a performance hit by doing so because now the integrator is forced to stop at every saving point, but this is guerenteed to match the order of the integrator even with the ManifoldProjection.

## References

[1] Ernst Hairer, Christian Lubich, Gerhard Wanner. Geometric Numerical Integration: Structure-Preserving Algorithms for Ordinary Differential Equations. Berlin ; New York :Springer, 2002.
