```
project(G::Graphs.SimpleGraph;  membership::Vector=Graphs.bipartite_map(G), 
                                bottom::Vector=findall(membership .== 1), 
                                top::Vector=findall(membership .== 2); 
                                layer::Symbol=:bottom)
```

Project the bipartite graph `G` onto one of its layers and return the projected graph.

# Arguments

  * `membership`: the bipartite mapping of the graphs. This can be computed using `Graphs.bipartite_map(G)`.
  * `bottom`: the nodes in the bottom layer. This can be computed using `findall(membership .== 1)`.
  * `top`: the nodes in the top layer. This can be computed using `findall(membership .== 2)`.
  * `layer`: the layer can be specified by passing `layer=:bottom` or `layer=:top`. Layer membership is determined by the bipartite map of the graph.
  * `method`: the method used to compute the adjacency matrix of the projected graph. This can be `:simple` or `:weighted`. Both methods compute    the product of the biadjacency matrix with its transposed, but the `:weighted` method uses the weights of the edges in the projected graph.

# Examples

```jldoctest project_bipartite_to_simple
julia> using Graphs

julia> G = SimpleGraph(5); add_edge!(G, 1, 4); add_edge!(G, 2, 4); add_edge!(G, 3, 4); add_edge!(G, 3, 5);

julia> project(G, layer=:bottom)
{3, 3} undirected simple Int64 graph

```

```jldoctest project_bipartite_to_simple
julia> project(G, layer=:top)
{2, 1} undirected simple Int64 graph

```
