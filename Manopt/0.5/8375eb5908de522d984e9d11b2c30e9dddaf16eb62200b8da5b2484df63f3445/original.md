```
get_inequality_constraint(amp::AbstractManoptProblem, p, j=:)
get_inequality_constraint(M::AbstractManifold, co::ConstrainedManifoldObjective, p, j=:, range=NestedPowerRepresentation())
```

Evaluate inequality constraints of a [`ConstrainedManifoldObjective`](@ref) `objective` at point `p` and indices `j` (by default `:` which corresponds to all indices).
