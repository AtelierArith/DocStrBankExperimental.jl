```
erdos_renyi(n, p)
```

Create an [Erdős–Rényi](http://en.wikipedia.org/wiki/Erdős–Rényi_model) random graph with `n` vertices. Edges are added between pairs of vertices with probability `p`.

### Optional Arguments

  * `is_directed=false`: if true, return a directed graph.
  * `seed=-1`: set the RNG seed.

# Examples

```jldoctest
julia> erdos_renyi(10, 0.5)
{10, 20} undirected simple Int64 graph

julia> erdos_renyi(10, 0.5, is_directed=true, seed=123)
{10, 49} directed simple Int64 graph
```
