```
wedges(G::Graphs.SimpleGraph)
wedges(A::T; check_dimensions::Bool=true, check_directed::Bool=true) where {T<:AbstractMatrix}
wedges(m::UBCM)
```

Compute the number of (expected) wedges for an undirected graph. Can be done directly from the graph, based on the adjacency matrix or a UBCM model.

# Arguments

For the adjacency matrix `A`, the following arguments can be passed:

  * `check_dimensions`: if true, check that `A` is a square matrix, otherwise throw an error.
  * `check_directed`: if true, check that `A` is symmetrical, otherwise throw an error.

# Examples

```jldoctest wedges_graph_docs
julia> G = MaxEntropyGraphs.Graphs.smallgraph(:karate);

julia> model = UBCM(G);

julia> solve_model!(model);

julia> set_Ĝ!(model);

julia> (wedges(G), wedges(MaxEntropyGraphs.Graphs.adjacency_matrix(G)), wedges(model))
(528.0, 528.0, 528.0000011499742)
```
