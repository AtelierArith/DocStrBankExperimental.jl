```
erdos_renyi(n, p::Real)
```

Create an [Erdős–Rényi](http://en.wikipedia.org/wiki/Erdős–Rényi_model) random graph with `n` vertices. Edges are added between pairs of vertices with probability `p`. 

Note that there exists another definition of the Erdös-Rényi model in which the total number of edges is kept constant, rather than the probability `p`. To access this definition, use `erdos_renyi(n, ne::Integer)` (specifically: `erdos_renyi(n, 1) != erdos_renyi(n, 1.0)`).

### Optional Arguments

  * `is_directed=false`: if true, return a directed graph.
  * `rng=nothing`: set the Random Number Generator.
  * `seed=nothing`: set the RNG seed.

# Examples

```
julia> using Graphs

julia> erdos_renyi(10, 0.5)
{10, 20} undirected simple Int64 graph
```

```
julia> using Graphs

julia> erdos_renyi(10, 0.5, is_directed=true, seed=123)
{10, 49} directed simple Int64 graph
```
