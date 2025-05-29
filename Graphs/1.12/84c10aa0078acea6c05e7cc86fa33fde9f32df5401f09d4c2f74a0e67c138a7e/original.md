```
assortativity(g)
```

Return the [assortativity coefficient](https://en.wikipedia.org/wiki/Assortativity) of graph `g`, defined as the Pearson correlation of excess degree between the end vertices of all the edges of the graph.

The excess degree is equal to the degree of linked vertices minus one, i.e. discounting the edge that links the pair. In directed graphs, the paired values are the out-degree of source vertices and the in-degree of destination vertices.

# Examples

```jldoctest
julia> using Graphs

julia> assortativity(star_graph(4))
-1.0
```
