```
ANND(A::T, i::Int; check_dimensions::Bool=true, check_directed::Bool=true) where {T<:AbstractMatrix}
```

Compute the average nearest neighbor degree (ANND) for node `i` using adjacency matrix `A`. The ANND for a node `i` is defined as $ANND_i(A^{*}) = \frac{\sum_{j=1}^{N} a_{ij}k_j }{k_i}$ where $a_{ij}$ denotes the element of the adjacency matrix $A$ at row $i$ and column $j$, and $k_i$ denotes the degree of node $i$.

**Notes:** 

  * this function is intented for use with the expected adjacency matrix of a `::AbstractMaxEntropyModel` model. A separate method exists for `::AbstractGraph` objects.
  * if `A` is not symmetrical, you have a directed graph, and this will throw an error by default. This can be turned off by setting `check_directed=false`.
  * the adjacency matrix should be square, if not, this will throw an error by default. This can be turned off by setting `check_dimensions=false`.

# Examples

```jldoctest ANND_mat_node_docs
julia> using Graphs

julia> G = smallgraph(:karate);

julia> A = adjacency_matrix(G);

julia> ANND(A, 1)
4.3125

```

```jldoctest ANND_mat_node_docs
julia> Gd = SimpleDiGraph(G);

julia> add_vertex!(Gd); add_edge!(Gd, 1, nv(Gd));

julia> Ad = adjacency_matrix(Gd);

julia> ANND(Ad, 1)
ERROR: ArgumentError: The matrix is not symmetrical. Consider using ANND_in or ANND_out instead.
[...]
```

```jldoctest ANND_mat_node_docs
julia> ANND(Ad, 1, check_directed=false)
4.375

```

```jldoctest ANND_mat_node_docs
julia> ANND(rand(2,3),1)
ERROR: DimensionMismatch: `A` must be a square matrix.
[...]
```

See also: `ANND_in`, `ANND_out`, [`Graphs.degree`](https://juliagraphs.org/Graphs.jl/stable/core_functions/core/#Graphs.degree)
