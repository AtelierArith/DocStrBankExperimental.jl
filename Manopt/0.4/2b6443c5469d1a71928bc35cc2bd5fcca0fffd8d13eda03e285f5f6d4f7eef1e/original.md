```
get_equality_constraint(M::AbstractManifold, emo::EmbeddedManifoldObjective, p, j)
```

evaluate the `j`s equality constraint $h_j(p)$ defined in the embedding, that is embed `p` before calling the constraint functions stored in the [`EmbeddedManifoldObjective`](@ref).
