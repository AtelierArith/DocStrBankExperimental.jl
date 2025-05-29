```
get_hess_equality_constraint(amp::AbstractManoptProblem, p, j=:)
get_hess_equality_constraint(M::AbstractManifold, co::ConstrainedManifoldObjective, p, j, range=NestedPowerRepresentation())
get_hess_equality_constraint!(amp::AbstractManoptProblem, X, p, j=:)
get_hess_equality_constraint!(M::AbstractManifold, X, co::ConstrainedManifoldObjective, p, j, range=NestedPowerRepresentation())
```

Evaluate the Hessian or Hessians of the equality constraint $(\operatorname{Hess} h(p))_j$ or $\operatorname{Hess} h_j(p)$,

See also the [`ConstrainedManoptProblem`](@ref) to specify the range of the Hessian.
