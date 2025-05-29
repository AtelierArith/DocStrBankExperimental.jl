```
squares(G::Graphs.SimpleGraph)
squares(A::T; check_dimensions::Bool=true, check_directed::Bool=true) where {T<:AbstractMatrix}
squares(m::UBCM)
```

Compute the number of (expected) squares for an undirected graph. Can be done directly from the graph, based on the adjacency matrix or a UBCM model.

# Notes:

In this function, by $square$, a 'pure' square is understood, without any diagonals inside. This explains the difference with the induced subgraph count, which counts all squares, including those with triangles inside. 

# Arguments

For the adjacency matrix `A`, the following arguments can be passed:

  * `check_dimensions`: if true, check that `A` is a square matrix, otherwise throw an error.
  * `check_directed`: if true, check that `A` is symmetrical, otherwise throw an error.

These checks can be turned off for perfomance reasons.

# Examples

```jldoctest squares_doc_all
julia> G = MaxEntropyGraphs.Graphs.smallgraph(:karate);

julia> model = UBCM(G);

julia> solve_model!(model);

julia> set_Ĝ!(model);

julia> (squares(G), squares(MaxEntropyGraphs.Graphs.adjacency_matrix(G)), squares(model))
(36.0, 36.0, 45.644736823949344)
```
