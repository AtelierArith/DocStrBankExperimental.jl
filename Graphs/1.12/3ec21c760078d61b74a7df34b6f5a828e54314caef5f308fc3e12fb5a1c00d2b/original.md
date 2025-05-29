```
spfa_shortest_paths(g, s, distmx=weights(g))
```

Compute shortest paths between a source `s` and all other nodes in graph `g` using the [Shortest Path Faster Algorithm](https://en.wikipedia.org/wiki/Shortest_Path_Faster_Algorithm).

Return a vector of distances to the source.

# Examples

```jldoctest
julia> using Graphs

julia> g = complete_graph(4);

julia> d = [1 1 -1 1; 1 1 -1 1; 1 1 1 1; 1 1 1 1];

julia> spfa_shortest_paths(g, 1, d)
4-element Vector{Int64}:
  0
  0
 -1
  0
```

```jldoctest
julia> using Graphs

julia> g = complete_graph(3);

julia> d = [1 -3 1; -3 1 1; 1 1 1];

julia> spfa_shortest_paths(g, 1, d)
ERROR: Graphs.NegativeCycleError()
[...]
```
