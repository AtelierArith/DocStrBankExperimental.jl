```
GNNHeteroGraph(data; [ndata, edata, gdata, num_nodes])
GNNHeteroGraph(pairs...; [ndata, edata, gdata, num_nodes])
```

A type representing a heterogeneous graph structure. It is similar to [`GNNGraph`](@ref) but nodes and edges are of different types.

# Constructor Arguments

  * `data`: A dictionary or an iterable object that maps `(source_type, edge_type, target_type)`         triples to `(source, target)` index vectors (or to `(source, target, weight)` if also edge weights are present).
  * `pairs`: Passing multiple relations as pairs is equivalent to passing `data=Dict(pairs...)`.
  * `ndata`: Node features. A dictionary of arrays or named tuple of arrays.          The size of the last dimension of each array must be given by `g.num_nodes`.
  * `edata`: Edge features. A dictionary of arrays or named tuple of arrays. Default `nothing`.          The size of the last dimension of each array must be given by `g.num_edges`. Default `nothing`.
  * `gdata`: Graph features. An array or named tuple of arrays whose last dimension has size `num_graphs`. Default `nothing`.
  * `num_nodes`: The number of nodes for each type. If not specified, inferred from `data`. Default `nothing`.

# Fields

  * `graph`: A dictionary that maps `(source_type, edge_type, target_type)` triples to `(source, target)` index vectors.
  * `num_nodes`: The number of nodes for each type.
  * `num_edges`: The number of edges for each type.
  * `ndata`: Node features.
  * `edata`: Edge features.
  * `gdata`: Graph features.
  * `ntypes`: The node types.
  * `etypes`: The edge types.

# Examples

```julia
julia> using GNNGraphs

julia> nA, nB = 10, 20;

julia> num_nodes = Dict(:A => nA, :B => nB);

julia> edges1 = (rand(1:nA, 20), rand(1:nB, 20))
([4, 8, 6, 3, 4, 7, 2, 7, 3, 2, 3, 4, 9, 4, 2, 9, 10, 1, 3, 9], [6, 4, 20, 8, 16, 7, 12, 16, 5, 4, 6, 20, 11, 19, 17, 9, 12, 2, 18, 12])

julia> edges2 = (rand(1:nB, 30), rand(1:nA, 30))
([17, 5, 2, 4, 5, 3, 8, 7, 9, 7  …  19, 8, 20, 7, 16, 2, 9, 15, 8, 13], [1, 1, 3, 1, 1, 3, 2, 7, 4, 4  …  7, 10, 6, 3, 4, 9, 1, 5, 8, 5])

julia> data = ((:A, :rel1, :B) => edges1, (:B, :rel2, :A) => edges2);

julia> hg = GNNHeteroGraph(data; num_nodes)
GNNHeteroGraph:
  num_nodes: (:A => 10, :B => 20)
  num_edges: ((:A, :rel1, :B) => 20, (:B, :rel2, :A) => 30)

julia> hg.num_edges
Dict{Tuple{Symbol, Symbol, Symbol}, Int64} with 2 entries:
(:A, :rel1, :B) => 20
(:B, :rel2, :A) => 30

# Let's add some node features
julia> ndata = Dict(:A => (x = rand(2, nA), y = rand(3, num_nodes[:A])),
                    :B => rand(10, nB));

julia> hg = GNNHeteroGraph(data; num_nodes, ndata)
GNNHeteroGraph:
    num_nodes: (:A => 10, :B => 20)
    num_edges: ((:A, :rel1, :B) => 20, (:B, :rel2, :A) => 30)
    ndata:
    :A  =>  (x = 2×10 Matrix{Float64}, y = 3×10 Matrix{Float64})
    :B  =>  x = 10×20 Matrix{Float64}

# Access features of nodes of type :A
julia> hg.ndata[:A].x
2×10 Matrix{Float64}:
    0.825882  0.0797502  0.245813  0.142281  0.231253  0.685025  0.821457  0.888838  0.571347   0.53165
    0.631286  0.316292   0.705325  0.239211  0.533007  0.249233  0.473736  0.595475  0.0623298  0.159307
```

See also [`GNNGraph`](@ref) for a homogeneous graph type and [`rand_heterograph`](@ref) for a function to generate random heterographs.
