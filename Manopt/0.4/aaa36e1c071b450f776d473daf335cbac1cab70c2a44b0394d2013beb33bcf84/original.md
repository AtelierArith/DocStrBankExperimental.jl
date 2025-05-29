```
EmbeddedManifoldObjective{P, T, E, O2, O1<:AbstractManifoldObjective{E}} <:
   AbstractDecoratedManifoldObjective{E,O2}
```

Declare an objective to be defined in the embedding. This also declares the gradient to be defined in the embedding, and especially being the Riesz representer with respect to the metric in the embedding. The types can be used to still dispatch on also the undecorated objective type `O2`.

# Fields

  * `objective`: the objective that is defined in the embedding
  * `p`:         (`nothing`) a point in the embedding.
  * `X`:         (`nothing`) a tangent vector in the embedding

When a point in the embedding `p` is provided, `embed!` is used in place of this point to reduce memory allocations. Similarly `X` is used when embedding tangent vectors
