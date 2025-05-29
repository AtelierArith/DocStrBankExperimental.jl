```
FeaturedGraph(g, [mt]; directed=:auto, nf, ef, gf, pf=nothing,
    T, N, E, with_batch=false)
```

A type representing a graph structure and storing also arrays that contain features associated to nodes, edges, and the whole graph.

A `FeaturedGraph` can be constructed out of different objects `g` representing the connections inside the graph. When constructed from another featured graph `fg`, the internal graph representation is preserved and shared.

# Arguments

  * `g`: Data representing the graph topology. Possible type are

      * An adjacency matrix.
      * An adjacency list.
      * A Graphs' graph, i.e. `SimpleGraph`, `SimpleDiGraph` from Graphs, or `SimpleWeightedGraph`,   `SimpleWeightedDiGraph` from SimpleWeightedGraphs.
      * An `AbstractFeaturedGraph` object.
  * `mt::Symbol`: Matrix type for `g` in matrix form. if `graph` is in matrix form, `mt` is   recorded as one of `:adjm`, `:normedadjm`, `:laplacian`, `:normalized` or `:scaled`.
  * `directed`: It specify that direction of a graph. It can be `:auto`, `:directed` and   `:undirected`. Default value is `:auto`, which infers direction automatically.
  * `nf`: Node features.
  * `ef`: Edge features.
  * `gf`: Global features.
  * `pf`: Positional features. If `nothing` is given, positional encoding is turned off. If an   array is given, positional encoding is assigned as given array. If `:auto` is given,   positional encoding is generated automatically for node features and `with_batch` is considered.
  * `T`: It specifies the element type of graph. Default value is the element type of `g`.
  * `N`: Number of nodes for `g`.
  * `E`: Number of edges for `g`.
  * `with_batch::Bool`: Consider last dimension of all features as batch dimension.

# Usage

```
using GraphSignals, CUDA

# Construct from adjacency list representation
g = [[2,3], [1,4,5], [1], [2,5], [2,4]]
fg = FeaturedGraph(g)

# Number of nodes and edges
nv(fg)  # 5
ne(fg)  # 10

# From a Graphs' graph
fg = FeaturedGraph(erdos_renyi(100, 20))

# Copy featured graph while also adding node features
fg = FeaturedGraph(fg, nf=rand(100, 5))

# Send to gpu
fg = fg |> cu
```

See also [`graph`](@ref), [`node_feature`](@ref), [`edge_feature`](@ref), and [`global_feature`](@ref).
