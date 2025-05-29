```
ANND(G::T, i::Int; check_directed::Bool=true) where {T<:Graphs.AbstractGraph}
```

Compute the average nearest neighbor degree (ANND) for node `i` in graph `G`. The ANND for a node `i` is defined as $ANND_i(A^{*}) = \frac{\sum_{j=1}^{N} a_{ij}k_j }{k_i}$ where $a_{ij}$ denotes the element of the adjacency matrix $A$ at row $i$ and column $j$, and $k_i$ denotes the degree of node $i$.

**Notes:** 

  * the ANND is only defined for nodes with nonzero degree. If `degree(G,i) = 0`, then `ANND(G,i) = 0`.
  * if `G` is a directed graph, by default an error is thrown because the `degree` function returns the incoming plus outgoing edges for node `i` in this case.   This can be turned off by setting `check_directed=false`.

# Examples

```jldoctest ANND_graph_node_docs
julia> using Graphs

julia> G = smallgraph(:karate);

julia> ANND(G,1)
4.3125

```

```jldoctest ANND_graph_node_docs
julia> add_vertex!(G);

julia> ANND(G, nv(G))
0.0
```

```jldoctest ANND_graph_node_docs
julia> Gd = SimpleDiGraph(G);

julia> ANND(Gd,1)
ERROR: ArgumentError: The graph is directed. The degree function returns the incoming plus outgoing edges for node `i`. Consider using ANND_in or ANND_out instead.
[...]
```

```jldoctest ANND_graph_node_docs
julia> ANND(Gd,1, check_directed=false)
4.3125
```

See also: [`ANND_in`](@ref), [`ANND_out`](@ref), [`Graphs.degree`](https://juliagraphs.org/Graphs.jl/stable/core_functions/core/#Graphs.degree)
