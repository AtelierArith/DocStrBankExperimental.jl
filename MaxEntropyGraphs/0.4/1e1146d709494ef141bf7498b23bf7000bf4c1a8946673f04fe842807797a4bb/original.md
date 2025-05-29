```
ANND(G::T, vs=vertices(G); check_directed::Bool=true) where {T<:Graphs.AbstractGraph}
```

Return a vector correcponding to the average nearest neighbor degree (ANND) all nodes in the graph `G`.  If v is specified, only return the ANND for nodes in v. The ANND for a node `i` is defined as  $ANND_i(A^{*}) = \frac{\sum_{j=1}^{N} a_{ij}k_j }{k_i}$ where $a_{ij}$ denotes the element of the adjacency matrix $A$ at row $i$ and column $j$, and $k_i$ denotes the degree of node $i$.

**Notes:** 

  * the ANND is only defined for nodes with nonzero degree. If `degree(G,i) = 0`, then `ANND(G,i) = 0`.
  * if `G` is a directed graph, by default an error is thrown because the `degree` function returns the incoming plus outgoing edges for node `i` in this case.

This can be turned off by setting `check_directed=false`. This check is only performed once the actual computing.

# Examples

```jldoctest ANND_graph_docs
julia> using Graphs

julia> G = smallgraph(:karate);

julia> ANND(G,[10; 20; 30])
3-element Vector{Float64}:
 13.5
 14.0
  9.0

```

```jldoctest ANND_graph_docs
julia> Gd = SimpleDiGraph(G);

julia> ANND(Gd,[10; 20; 30]);
ERROR: ArgumentError: The graph is directed. The degree function returns the incoming plus outgoing edges for node `i`. Consider using ANND_in or ANND_out instead.
[...]
```

```jldoctest ANND_graph_docs
julia> ANND(Gd,[10; 20; 30], check_directed=false)
3-element Vector{Float64}:
 13.5
 14.0
  9.0

```

See also: `ANND_in`, `ANND_out`, [`Graphs.degree`](https://juliagraphs.org/Graphs.jl/stable/core_functions/core/#Graphs.degree)
