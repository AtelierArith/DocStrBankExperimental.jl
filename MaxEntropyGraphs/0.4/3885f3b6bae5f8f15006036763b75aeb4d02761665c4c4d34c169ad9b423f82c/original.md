```
triangles(G::Graphs.SimpleGraph)
triangles(A::T; check_dimensions::Bool=true, check_directed::Bool=true) where {T<:AbstractMatrix}
triangles(m::UBCM)
```

Compute the number of (expected) triangles for an undirected graph. Can be done directly from the graph, based on the adjacency matrix or a UBCM model.

# Arguments

For the adjacency matrix `A`, the following arguments can be passed:

  * `check_dimensions`: if true, check that `A` is a square matrix, otherwise throw an error.
  * `check_directed`: if true, check that `A` is symmetrical, otherwise throw an error.

These checks can be turned off for perfomance reasons.

# Examples

```jldoctest triangles_doc_all
julia> G = MaxEntropyGraphs.Graphs.smallgraph(:karate);

julia> model = UBCM(G);

julia> solve_model!(model);

julia> set_Ĝ!(model);

julia> (triangles(G), triangles(MaxEntropyGraphs.Graphs.adjacency_matrix(G)), triangles(model))
(45, 45.0, 52.849301363026846)
```
