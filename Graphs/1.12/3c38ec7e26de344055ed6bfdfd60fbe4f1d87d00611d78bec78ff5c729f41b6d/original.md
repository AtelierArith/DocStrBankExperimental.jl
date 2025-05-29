```
savegraph(file, d, format=LGFormat())
```

Save a dictionary `d` of `graphname => graph` to `file` in the format `format`. Return the number of graphs written.

# Examples

```jldoctest
julia> using Graphs

julia> g1 = SimpleGraph(5,8)
{5, 8} undirected simple Int64 graph

julia> g2 = SimpleGraph(7,10)
{7, 10} undirected simple Int64 graph

julia> d = Dict("graph_1" => g1, "graph_2" => g2);

julia> savegraph("myfile.txt", d, LGFormat())
2
```

### Implementation Notes

Will only work if the file format supports multiple graph types.
