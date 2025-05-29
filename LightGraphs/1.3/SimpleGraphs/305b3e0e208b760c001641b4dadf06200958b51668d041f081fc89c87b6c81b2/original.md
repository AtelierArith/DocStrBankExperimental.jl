```
star_digraph(n)
```

Create a directed [star graph](https://en.wikipedia.org/wiki/Star_(graph_theory)) with `n` vertices.

# Examples

```jldoctest
julia> star_digraph(3)
{3, 2} directed simple Int64 graph

julia> star_digraph(Int8(10))
{10, 9} directed simple Int8 graph
```
