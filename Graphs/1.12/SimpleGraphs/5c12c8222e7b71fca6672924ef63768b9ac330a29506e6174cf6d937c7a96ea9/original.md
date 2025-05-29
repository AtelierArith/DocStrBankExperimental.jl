```
erdos_renyi(n, ne::Integer)
```

Create an [Erdős–Rényi](http://en.wikipedia.org/wiki/Erdős–Rényi_model) random graph with `n` vertices and `ne` edges.

### Optional Arguments

  * `is_directed=false`: if true, return a directed graph.
  * `rng=nothing`: set the Random Number Generator.
  * `seed=nothing`: set the RNG seed.

# Examples

```
julia> using Graphs

julia> erdos_renyi(10, 30)
{10, 30} undirected simple Int64 graph

julia> erdos_renyi(10, 30, is_directed=true, seed=123)
{10, 30} directed simple Int64 graph
```
