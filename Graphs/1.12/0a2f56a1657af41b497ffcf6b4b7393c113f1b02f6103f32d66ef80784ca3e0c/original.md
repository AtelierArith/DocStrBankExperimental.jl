```
global_clustering_coefficient(g)
```

Return the [global clustering coefficient](https://en.wikipedia.org/wiki/Clustering_coefficient) of graph `g`.

# Examples

```jldoctest
julia> using Graphs

julia> global_clustering_coefficient(star_graph(4))
0.0

julia> global_clustering_coefficient(smallgraph(:housex))
0.7894736842105263
```
