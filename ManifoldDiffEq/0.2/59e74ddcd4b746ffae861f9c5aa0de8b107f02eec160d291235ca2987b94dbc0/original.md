```
ManifoldODEProblem
```

A general problem for ODE problems on Riemannian manifolds.

# Fields

  * `f` the tangent vector field `f(u,p,t)`
  * `u0` the initial condition
  * `tspan` time interval for the solution
  * `p` constant parameters for `f``
  * `kwargs` A callback to be applied to every solver which uses the problem.
  * `problem_type` type of problem
  * `manifold` the manifold the vector field is defined on
