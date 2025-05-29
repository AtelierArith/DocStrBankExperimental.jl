```julia
struct TreeBelief{T<:DistributedFactorGraphs.InferenceVariable, P, M<:ManifoldsBase.AbstractManifold}
```

INTERMEDIATE DATA STRUCTURE DURING REFACTORING.

Representation of the belief of a single variable.

Notes:

  * we want to send the joint, this is just to resolve consolidation #459 first.
  * Long term objective is single joint definition, likely called `LikelihoodMessage`.
