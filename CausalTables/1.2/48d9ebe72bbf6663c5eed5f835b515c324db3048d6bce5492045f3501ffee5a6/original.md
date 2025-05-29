```
KOrderStatistics <: NetworkSummary
```

A NetworkSummary which computes the top K ordered values of the target variable among each unit's connected neighbors in the adjacency `matrix`.

# Fields

  * `target::Symbol`: A key denoting the target variable to be summarized in the `DataGeneratingProcess` of the `StructuralCausalModel`; or, alternatively, the target variable to be summarized in the `data` attribute of a `CausalTable`.
  * `matrix::Symbol`: A key denoting the adjacency matrix over which summary is computed in the `DataGeneratingProcess` of the `StructuralCausalModel`; or, alternatively, the key of the adjacency matrix in the `arrays` attribute of a `CausalTable`.
  * `weights::Union{Symbol, Nothing}`: An optional variable by which each unit may be weighted in the summary.
