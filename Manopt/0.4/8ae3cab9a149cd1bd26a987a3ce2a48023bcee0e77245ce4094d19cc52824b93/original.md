```
get_inequality_constraint(M::AbstractManifold, ems::EmbeddedManifoldObjective, p, i)
```

Evaluate the `i`s inequality constraint $g_i(p)$ defined in the embedding, that is embed `p` before calling the constraint functions stored in the [`EmbeddedManifoldObjective`](@ref).
