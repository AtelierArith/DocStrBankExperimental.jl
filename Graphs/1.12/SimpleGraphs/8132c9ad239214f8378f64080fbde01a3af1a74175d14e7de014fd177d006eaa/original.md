```
euclidean_graph(N, d; rng=nothing, seed=nothing, L=1., p=2., cutoff=-1., bc=:open)
```

Generate `N` uniformly distributed points in the box $[0,L]^{d}$ and return a Euclidean graph, a map containing the distance on each edge and a matrix with the points' positions.

## Examples

```
julia> using Graphs

julia> g, dists = euclidean_graph(5, 2, cutoff=0.3);

julia> g
{5, 4} undirected simple Int64 graph

julia> dists
Dict{Graphs.SimpleGraphs.SimpleEdge{Int64},Float64} with 4 entries:
  Edge 1 => 5 => 0.205756
  Edge 2 => 5 => 0.271359
  Edge 2 => 4 => 0.247703
  Edge 4 => 5 => 0.168372
```
