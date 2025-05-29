```
get_equality_constraint(amp::AbstractManoptProblem, p, j=:)
get_equality_constraint(M::AbstractManifold, objective, p, j=:)
```

Evaluate equality constraints of a [`ConstrainedManifoldObjective`](@ref) `objective` at point `p` and indices `j` (by default `:` which corresponds to all indices).
