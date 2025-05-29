This function wrap from [NetworkX](https://github.com/networkx/networkx)

Position nodes using the eigenvectors of the graph Laplacian.

**Parameters**

*g* a graph

*weight* array or nothing, optional (default=nothing) The edge attribute that holds the numerical value used for the edge weight.  If None, then all edge weights are 1.

**Examples**

```
julia> g = smallgraph(:karate)
julia> weight = rand(ne(g))
julia> locs_x, locs_y = spectral_layout(g, weight)
```
