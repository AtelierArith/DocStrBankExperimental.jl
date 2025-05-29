```
get_cost(M::AbstractManifold,emo::EmbeddedManifoldObjective, p)
```

Evaluate the cost function of an objective defined in the embedding by first embedding `p` before calling the cost function stored in the [`EmbeddedManifoldObjective`](@ref).
