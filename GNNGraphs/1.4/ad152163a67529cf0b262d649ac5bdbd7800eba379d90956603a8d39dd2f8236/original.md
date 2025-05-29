```
get_graph_type(g::GNNGraph)
```

Return the underlying representation for the graph `g` as a symbol.

Possible values are:

  * `:coo`: Coordinate list representation. The graph is stored as a tuple of vectors `(s, t, w)`,         where `s` and `t` are the source and target nodes of the edges, and `w` is the edge weights.
  * `:sparse`: Sparse matrix representation. The graph is stored as a sparse matrix representing the weighted adjacency matrix.
  * `:dense`: Dense matrix representation. The graph is stored as a dense matrix representing the weighted adjacency matrix.

The default representation for graph constructors GNNGraphs.jl is `:coo`. The underlying representation can be accessed through the `g.graph` field.

See also [`GNNGraph`](@ref).

# Examples

The default representation for graph constructors GNNGraphs.jl is `:coo`.

```jldoctest
julia> g = rand_graph(5, 10)
GNNGraph:
  num_nodes: 5
  num_edges: 10

julia> get_graph_type(g)
:coo
```

The `GNNGraph` constructor can also be used to create graphs with different representations.

```jldoctest
julia> g = GNNGraph([2,3,5], [1,2,4], graph_type=:sparse)
GNNGraph:
  num_nodes: 5
  num_edges: 3

julia> g.graph
5×5 SparseArrays.SparseMatrixCSC{Int64, Int64} with 3 stored entries:
 ⋅  ⋅  ⋅  ⋅  ⋅
 1  ⋅  ⋅  ⋅  ⋅
 ⋅  1  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  1  ⋅

julia> get_graph_type(g)
:sparse

julia> gcoo = GNNGraph(g, graph_type=:coo);

julia> gcoo.graph
([2, 3, 5], [1, 2, 4], [1, 1, 1])
```
