```
binary_tree(k::Integer)
```

Create a [binary tree](https://en.wikipedia.org/wiki/Binary_tree) of depth `k`.

# Examples

```jldoctest
julia> using Graphs

julia> binary_tree(4)
{15, 14} undirected simple Int64 graph

julia> binary_tree(Int8(5))
{31, 30} undirected simple Int8 graph
```
