```
random_tournament_digraph(n)
```

Create a random directed [tournament graph](https://en.wikipedia.org/wiki/Tournament_%28graph_theory%29) with `n` vertices.

### Optional Arguments

  * `seed=-1`: set the RNG seed.

# Examples

```jldoctest
julia> random_tournament_digraph(5)
{5, 10} directed simple Int64 graph

julia> random_tournament_digraph(Int8(10), seed=123)
{10, 45} directed simple Int8 graph
```
