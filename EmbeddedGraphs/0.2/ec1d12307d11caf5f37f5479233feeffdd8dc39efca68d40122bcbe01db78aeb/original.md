```
random_geometric_graph!(eg, radius; dist_func=Nothing)
```

From an existing embedded complete graph `eg`, create a [random geometric graph](http://en.wikipedia.org/wiki/Random_geometric_graph) by removing edges between vertices that are more than `radius` apart. This in-place graph generator offers more flexibility with respect to the properties of the resulting EmbeddedGraph instance `eg`. For instance, the embedding metric determining the values of `weights(eg)` can be distinct from the distance function `dist_func` that is used to  create the random geometric graph.

Ref.: Penrose, Mathew. Random geometric graphs. Vol. 5. Oxford university press, 2003.

### Optional Arguments

  * `dist_func`: distance function used to construct the random geometric graph. It can differ from the `distance` attribute of `eg` to allow for independent edge weights. Defaults to `eg.distance` when `dist_func=Nothing` is passed.

# Examples

```julia
julia> egh = EmbeddedGraph(complete_graph(n), pos, hamming);

julia> random_geometric_graph!(egh, rad; dist_func=euclidean)

julia> egh.graph
{50, 71} undirected simple Int64 graph
```
