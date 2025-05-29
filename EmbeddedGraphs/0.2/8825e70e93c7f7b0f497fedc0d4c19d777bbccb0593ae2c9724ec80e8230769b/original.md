```
random_geometric_graph(n, radius; dim=2, pos=Nothing, embedding_metric=Nothing, dist_func=Nothing)
```

Create a [random geometric graph](http://en.wikipedia.org/wiki/Random_geometric_graph) with `n` vertices that are connected when their distance is less than `radius`. The vertex locations are randomly drawn from a uniform distribution on the unit interval in each dimension.

Ref.: Penrose, Mathew. Random geometric graphs. Vol. 5. Oxford university press, 2003.

### Optional Arguments

  * `dim`: embedding dimension. Defaults to dim=2.
  * `pos`: vertex positions can be given as a list of `n` points with `dim` coordinates. Defaults to pos=Nothing.
  * `dist_func`: distance function used to construct the random geometric graph. It can differ from the `distance` attribute of `eg` to allow for independent edge weights. Defaults to `eg.distance` when `dist_func=Nothing` is passed.

# Examples

```julia
julia> random_geometric_graph(50, 0.2).graph
{50, 105} undirected simple Int64 graph
```
