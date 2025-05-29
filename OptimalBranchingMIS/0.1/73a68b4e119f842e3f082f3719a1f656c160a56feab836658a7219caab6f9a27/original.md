```
struct TensorNetworkReducer <: AbstractReducer
```

A reducer that uses tensor network contraction to find reduction rules.

# Fields

  * `n_max::Int = 15`: Maximum number of vertices to be included in the selected region
  * `selector::Symbol = :mincut`: Strategy for selecting vertices to contract. Options are:

      * `:neighbor`: Select vertices based on neighborhood
      * `:mincut`: Select vertices based on minimum cut provided by `KaHyPar` (as extension, requires `using KaHyPar`) !Note: `KaHyPar` may leads to memory leak!
  * `measure::AbstractMeasure = NumOfVertices()`: Measure used for kernelization. Uses size reduction from OptimalBranchingMIS
  * `intersect_strategy::Symbol = :bfs`: Strategy for intersecting clauses. Options are:

      * `:bfs`: Breadth-first search (gives the optimal result)
      * `:dfs`: Depth-first search (gives the first found non-zero intersection)
  * `sub_reducer::AbstractReducer = XiaoReducer()`: Reducer applied to selected vertices before tensor network contraction, default is XiaoReducer
