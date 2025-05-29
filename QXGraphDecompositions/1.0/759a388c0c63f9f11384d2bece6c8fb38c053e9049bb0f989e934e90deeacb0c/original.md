```
flow_cutter(G::lg.AbstractGraph, time::Integer=10; seed::Integer=-1)
```

Run the flow cutter algorithm for `time` seconds to find a tree decomposition for the graph  `G` with minimal treewidth.

The tree decomposition is returned in a dictionary with the following key value pairs:

  * `:treewidth` => The treewidth of the tree decomposotion,
  * `:num_bags` => The number of bags in the tree decomposition,
  * `:num_vertices` The number of vertices in `G`,
  * `:b_n` => The n-th bag of the decomposition where n is an integer from 1 to the number of            bags in the decomposition. A bag is an array of vertices of `G`.
  * `:edges` => An array of integer pairs indicating the edges of the tree decomposition.
  * `:comments` => An array of comments created by flow cutter regarding heuristics used and if                it had enough time to find a decomposition.

The flow cutter algorithm and how it is used to find tree decompositions is described by Michael Hamann and Ben Strasser in the following papers: 

Graph Bisection with Pareto Optimization - https://dl.acm.org/doi/10.1145/3173045 Computing Tree Decompositions with FlowCutter - https://arxiv.org/abs/1709.08949

# Keywords

  * `seed::Integer=-1`: The seed used by flow cutter. Most be a non negative integer,                     otherwise the seed is set by flow cutter.
