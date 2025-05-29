```
mis_branch_count(g::AbstractGraph; branching_strategy::BranchingStrategy = BranchingStrategy(table_solver = TensorNetworkSolver(), selector = MinBoundaryHighDegreeSelector(2, 6, 0), measure=D3Measure()), reducer=MISReducer(), show_progress::Bool = false)
```

Calculate the size and the number of branches of the Maximum Independent Set (MIS) for a given graph.

### Arguments

  * `g::AbstractGraph`: The graph for which the MIS size and the number of branches are to be calculated.

### Keyword Arguments

  * `branching_strategy::BranchingStrategy`: (optional) The branching strategy to be used. Defaults to a strategy using `table_solver=TensorNetworkSolver`, `selector=MinBoundaryHighDegreeSelector(2, 6, 0)`, and `measure=D3Measure`.
  * `reducer::AbstractReducer`: (optional) The reducer to be applied. Defaults to `MISReducer`.
  * `show_progress::Bool`: (optional) Whether to show the progress of the branching and reduction process. Defaults to `false`.

### Returns

  * A tuple `(size, count)` where `size` is the size of the Maximum Independent Set and `count` is the number of branches.
