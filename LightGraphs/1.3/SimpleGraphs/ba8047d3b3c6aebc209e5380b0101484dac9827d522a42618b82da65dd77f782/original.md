```
erdos_renyi(n, ne)
```

Create an [Erdős–Rényi](http://en.wikipedia.org/wiki/Erdős–Rényi_model) random graph with `n` vertices and `ne` edges.

### Optional Arguments

  * `is_directed=false`: if true, return a directed graph.
  * `seed=-1`: set the RNG seed.

# Examples

```jldoctest
julia> erdos_renyi(10, 30)
{10, 30} undirected simple Int64 graph

julia> erdos_renyi(10, 30, is_directed=true, seed=123)
{10, 30} directed simple Int64 graph
```
