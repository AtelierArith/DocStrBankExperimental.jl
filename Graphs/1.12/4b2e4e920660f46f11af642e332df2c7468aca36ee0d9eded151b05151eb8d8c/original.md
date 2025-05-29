```
size(g, i)
```

Return the number of vertices in `g` if `i`=1 or `i`=2, or `1` otherwise.

# Examples

```jldoctest
julia> using Graphs

julia> g = cycle_graph(4);

julia> size(g, 1)
4

julia> size(g, 2)
4

julia> size(g, 3)
1
```
