```
radius_graph(points::AbstractMatrix, 
             r::AbstractFloat; 
             graph_indicator = nothing,
             self_loops = false, 
             dir = :in, 
             kws...)
```

Create a graph where each node is linked  to its neighbors within a given distance `r`.  

# Arguments

  * `points`: A num*features × num*nodes matrix storing the Euclidean positions of the nodes.
  * `r`: The radius.
  * `graph_indicator`: Either nothing or a vector containing the graph assignment of each node,                     in which case the returned graph will be a batch of graphs.
  * `self_loops`: If `true`, consider the node itself among its neighbors, in which               case the graph will contain self-loops.
  * `dir`: The direction of the edges. If `dir=:in` edges go from the        neighbors to the central node. If `dir=:out` we have the opposite        direction.
  * `kws`: Further keyword arguments will be passed to the [`GNNGraph`](@ref) constructor.

# Examples

```julia
julia> n, r = 10, 0.75;

julia> x = rand(Float32, 3, n);

julia> g = radius_graph(x, r)
GNNGraph:
    num_nodes = 10
    num_edges = 46

julia> graph_indicator = [1,1,1,1,1,2,2,2,2,2];

julia> g = radius_graph(x, r; graph_indicator)
GNNGraph:
    num_nodes = 10
    num_edges = 20
    num_graphs = 2
```

# References

Section B paragraphs 1 and 2 of the paper [Dynamic Hidden-Variable Network Models](https://arxiv.org/pdf/2101.00414.pdf)
