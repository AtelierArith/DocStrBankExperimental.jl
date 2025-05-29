```
dijkstra_shortest_paths(g, srcs, distmx=weights(g));
```

Perform [Dijkstra's algorithm](http://en.wikipedia.org/wiki/Dijkstra%27s_algorithm) on a graph, computing shortest distances between `srcs` and all other vertices. Return a [`Graphs.DijkstraState`](@ref) that contains various traversal information (try querying `state.parents` or `state.dists`).

### Optional Arguments

  * `allpaths=false`: If true, `state.pathcounts` holds a vector, indexed by vertex, of the number of shortest paths from the source to that vertex. The path count of a source vertex is always `1.0`. The path count of an unreached vertex is always `0.0`.
  * `trackvertices=false`: If true, `state.closest_vertices` holds a vector of all vertices in the graph ordered from closest to farthest.
  * `maxdist` (default: `typemax(T)`) specifies the maximum path distance beyond which all path distances are assumed to be infinite (that is, they do not exist).

### Performance

If using a sparse matrix for `distmx`, you *may* achieve better performance by passing in a transpose of its sparse transpose. That is, assuming `D` is the sparse distance matrix:

```
D = transpose(sparse(transpose(D)))
```

Be aware that realizing the sparse transpose of `D` incurs a heavy one-time penalty, so this strategy should only be used when multiple calls to `dijkstra_shortest_paths` with the distance matrix are planned.

# Examples

```jldoctest
julia> using Graphs

julia> ds = dijkstra_shortest_paths(cycle_graph(5), 2);

julia> ds.dists
5-element Vector{Int64}:
 1
 0
 1
 2
 2

julia> ds = dijkstra_shortest_paths(path_graph(5), 2);

julia> ds.dists
5-element Vector{Int64}:
 1
 0
 1
 2
 3
```
