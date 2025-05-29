```
desopo_pape_shortest_paths(g, src, distmx=weights(g))
```

Compute shortest paths between a source `src` and all other nodes in graph `g` using the [D'Esopo-Pape algorithm](http://web.mit.edu/dimitrib/www/SLF.pdf). Return a [`Graphs.DEsopoPapeState`](@ref) with relevant traversal information (try querying `state.parents` or `state.dists`).

# Examples

```jldoctest
julia> using Graphs

julia> ds = desopo_pape_shortest_paths(cycle_graph(5), 2);

julia> ds.dists
5-element Vector{Int64}:
 1
 0
 1
 2
 2

julia> ds = desopo_pape_shortest_paths(path_graph(5), 2);

julia> ds.dists
5-element Vector{Int64}:
 1
 0
 1
 2
 3
```
