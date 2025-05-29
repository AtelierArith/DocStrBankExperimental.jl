Create a `Matroid` as follows:

  * `Matroid(m::Int, r::AbstractRankFunction)` given the number of elements and a rank function.
  * `Matroid(A::AbstractMatrix)` given a matrix.
  * `Matroid(g::Graph)` given a graph.
  * `Matroid(g::EasyMultiGraph)` given a multigraph.
  * `Matroid()` yields the matroid with no elements.

See also: `UniformMatroid`.
