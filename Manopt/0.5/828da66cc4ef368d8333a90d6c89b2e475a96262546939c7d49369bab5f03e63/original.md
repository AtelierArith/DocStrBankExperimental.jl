```
get_hess_inequality_constraint(amp::AbstractManoptProblem, p, X, j=:)
get_hess_inequality_constraint(M::AbstractManifold, co::ConstrainedManifoldObjective, p, j=:, range=NestedPowerRepresentation())
get_hess_inequality_constraint!(amp::AbstractManoptProblem, Y, p, j=:)
get_hess_inequality_constraint!(M::AbstractManifold, Y, co::ConstrainedManifoldObjective, p, X, j=:, range=NestedPowerRepresentation())
```

Evaluate the Hessian or Hessians of the inequality constraint $(\operatorname{Hess} g(p)[X])_j$ or $\operatorname{Hess} g_j(p)[X]$,

See also the [`ConstrainedManoptProblem`](@ref) to specify the range of the Hessian.
