```
turan_graph(n, r)
```

Creates a [Turán Graph](https://en.wikipedia.org/wiki/Tur%C3%A1n_graph), a complete multipartite graph with `n` vertices and `r` partitions.

# Examples

```jldoctest
julia> turan_graph(6, 2)
{6, 9} undirected simple Int64 graph

julia> turan_graph(Int8(7), 2)
{7, 12} undirected simple Int8 graph
```
