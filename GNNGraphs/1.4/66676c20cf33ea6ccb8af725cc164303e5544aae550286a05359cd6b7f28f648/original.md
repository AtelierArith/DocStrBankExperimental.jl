```
knn_graph(points::AbstractMatrix, 
          k::Int; 
          graph_indicator = nothing,
          self_loops = false, 
          dir = :in, 
          kws...)
```

Create a `k`-nearest neighbor graph where each node is linked  to its `k` closest `points`.  

# Arguments

  * `points`: A num*features × num*nodes matrix storing the Euclidean positions of the nodes.
  * `k`: The number of neighbors considered in the kNN algorithm.
  * `graph_indicator`: Either nothing or a vector containing the graph assignment of each node,                     in which case the returned graph will be a batch of graphs.
  * `self_loops`: If `true`, consider the node itself among its `k` nearest neighbors, in which               case the graph will contain self-loops.
  * `dir`: The direction of the edges. If `dir=:in` edges go from the `k`         neighbors to the central node. If `dir=:out` we have the opposite        direction.
  * `kws`: Further keyword arguments will be passed to the [`GNNGraph`](@ref) constructor.

# Examples

```julia
julia> n, k = 10, 3;

julia> x = rand(Float32, 3, n);

julia> g = knn_graph(x, k)
GNNGraph:
    num_nodes = 10
    num_edges = 30

julia> graph_indicator = [1,1,1,1,1,2,2,2,2,2];

julia> g = knn_graph(x, k; graph_indicator)
GNNGraph:
    num_nodes = 10
    num_edges = 30
    num_graphs = 2
```
