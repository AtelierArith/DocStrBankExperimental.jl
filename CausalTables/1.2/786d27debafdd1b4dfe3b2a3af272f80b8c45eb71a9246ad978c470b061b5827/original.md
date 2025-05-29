```
mutable struct Friends <: NetworkSummary
```

A NetworkSummary counting the number of connected individuals in an adjacency matrix, also known as the number of "friends".

# Fields

  * `matrix::Symbol`: A key denoting the adjacency matrix over which summary is computed in the `DataGeneratingProcess` of the `StructuralCausalModel`; or, alternatively, the key of the adjacency matrix in the `arrays` attribute of a `CausalTable`.
