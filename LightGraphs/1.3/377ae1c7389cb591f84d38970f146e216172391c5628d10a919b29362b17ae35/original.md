```
dijkstra_shortest_paths(g, srcs, distmx=weights(g));
```

Perform [Dijkstra's algorithm](http://en.wikipedia.org/wiki/Dijkstra%27s_algorithm) on a graph, computing shortest distances between `srcs` and all other vertices. Return a [`LightGraphs.DijkstraState`](@ref) that contains various traversal information.

### Optional Arguments

  * `allpaths=false`: If true, returns a [`LightGraphs.DijkstraState`](@ref) that keeps track of all

predecessors of a given vertex.

### Performance

If using a sparse matrix for `distmx`, you *may* achieve better performance by passing in a transpose of its sparse transpose. That is, assuming `D` is the sparse distance matrix:

```
D = transpose(sparse(transpose(D)))
```

Be aware that realizing the sparse transpose of `D` incurs a heavy one-time penalty, so this strategy should only be used when multiple calls to `dijkstra_shortest_paths` with the distance matrix are planned.

# Examples

```jldoctest
julia> using LightGraphs

julia> ds = dijkstra_shortest_paths(cycle_graph(5), 2);

julia> ds.dists
5-element Array{Int64,1}:
 1
 0
 1
 2
 2

julia> ds = dijkstra_shortest_paths(path_graph(5), 2);

julia> ds.dists
5-element Array{Int64,1}:
 1
 0
 1
 2
 3
```
