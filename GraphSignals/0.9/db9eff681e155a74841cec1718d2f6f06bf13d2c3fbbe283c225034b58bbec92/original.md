```
kneighbors_graph(X, k, metric; include_self=false, weighted=false)
kneighbors_graph(X, k; include_self=false, weighted=false)
```

Generate `k`-nearest neighborhood (kNN) graph from their node features. It returns a `FeaturedGraph` object, which contains a kNN graph and node features `X`.

# Arguments

  * `X::AbstractMatrix`: The feature matrix for each node with size `(feat_dim, num_nodes)`.
  * `k`: Number of nearest neighbor for each node in kNN graph.
  * `metric::Metric`: Distance metric to measure distance between any two nodes.

It aceepts distance objects from Distances.

  * `include_self::Bool`: Whether distance from node to itself is included in nearest neighbor.
  * `weighted::Bool`: Whether distance could be the edge weight in kNN graph.

# Usage

```jldoctest
julia> using GraphSignals, Distances

julia> nf = rand(Float32, 10, 1024);

julia> fg = kneighbors_graph(nf, 5)
FeaturedGraph:
	Directed graph with (#V=1024, #E=5120) in adjacency matrix
	Node feature:	ℝ^10 <Matrix{Float32}>

julia> fg = kneighbors_graph(nf, 5, Cityblock())
FeaturedGraph:
    Directed graph with (#V=1024, #E=5120) in adjacency matrix
    Node feature:	ℝ^10 <Matrix{Float32}>

julia> nf = rand(Float32[0, 1], 10, 1024);

julia> fg = kneighbors_graph(nf, 5, Jaccard(); include_self=true)
FeaturedGraph:
    Directed graph with (#V=1024, #E=5120) in adjacency matrix
    Node feature:	ℝ^10 <Matrix{Float32}>
```
