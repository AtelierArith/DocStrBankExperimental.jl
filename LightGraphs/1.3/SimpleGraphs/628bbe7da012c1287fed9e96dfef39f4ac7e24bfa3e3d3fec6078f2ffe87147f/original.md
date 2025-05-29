```
watts_strogatz(n, k, β)
```

Return a [Watts-Strogatz](https://en.wikipedia.org/wiki/Watts_and_Strogatz_model) small model random graph with `n` vertices, each with degree `k`. Edges are randomized per the model based on probability `β`.

### Optional Arguments

  * `is_directed=false`: if true, return a directed graph.
  * `seed=-1`: set the RNG seed.

## Examples

```jldoctest
julia> watts_strogatz(10, 4, 0.3)
{10, 20} undirected simple Int64 graph

julia> watts_strogatz(Int8(10), 4, 0.8, is_directed=true, seed=123)
{10, 20} directed simple Int8 graph
```
