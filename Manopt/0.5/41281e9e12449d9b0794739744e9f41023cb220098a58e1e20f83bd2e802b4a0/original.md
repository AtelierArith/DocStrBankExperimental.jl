```
get_grad_equality_constraint(amp::AbstractManoptProblem, p, j)
get_grad_equality_constraint(M::AbstractManifold, co::ConstrainedManifoldObjective, p, j, range=NestedPowerRepresentation())
get_grad_equality_constraint!(amp::AbstractManoptProblem, X, p, j)
get_grad_equality_constraint!(M::AbstractManifold, X, co::ConstrainedManifoldObjective, p, j, range=NestedPowerRepresentation())
```

Evaluate the gradient or gradients  of the equality constraint $(\operatorname{grad} h(p))_j$ or $\operatorname{grad} h_j(p)$,

See also the [`ConstrainedManoptProblem`](@ref) to specify the range of the gradient.
