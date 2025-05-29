```
period(g)
```

Return the (common) period for all vertices in a strongly connected directed graph. Will throw an error if the graph is not strongly connected.

# Examples

```jldoctest
julia> using Graphs

julia> g = SimpleDiGraph([0 1 0; 0 0 1; 1 0 0]);

julia> period(g)
3
```
