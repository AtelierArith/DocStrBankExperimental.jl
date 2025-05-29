```
color_refinement(g::GNNGraph, [x0]) -> x, num_colors, niters
```

The color refinement algorithm for graph coloring.  Given a graph `g` and an initial coloring `x0`, the algorithm  iteratively refines the coloring until a fixed point is reached.

At each iteration the algorithm computes a hash of the coloring and the sorted list of colors of the neighbors of each node. This hash is used to determine if the coloring has changed.

`math x_i' = hashmap((x_i, sort([x_j for j \in N(i)]))).``

This algorithm is related to the 1-Weisfeiler-Lehman algorithm for graph isomorphism testing.

# Arguments

  * `g::GNNGraph`: The graph to color.
  * `x0::AbstractVector{<:Integer}`: The initial coloring. If not provided, all nodes are colored with 1.

# Returns

  * `x::AbstractVector{<:Integer}`: The final coloring.
  * `num_colors::Int`: The number of colors used.
  * `niters::Int`: The number of iterations until convergence.
