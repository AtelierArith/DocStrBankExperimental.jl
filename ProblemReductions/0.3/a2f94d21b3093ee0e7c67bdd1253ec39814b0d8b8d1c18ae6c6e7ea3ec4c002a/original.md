```julia
struct Matching{T, WT<:AbstractArray{T, 1}} <: ProblemReductions.ConstraintSatisfactionProblem{T}
```

The [Vertex matching](https://queracomputing.github.io/GenericTensorNetworks.jl/dev/generated/Matching/) problem.

## Positional arguments

  * `graph` is the problem graph.
  * `weights` are associated with the edges of the `graph`.
