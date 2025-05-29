```
barabasi_albert!(g::AbstractGraph, n::Integer, k::Integer)
```

Create a [Barabási–Albert model](https://en.wikipedia.org/wiki/Barab%C3%A1si%E2%80%93Albert_model) random graph with `n` vertices. It is grown by adding new vertices to an initial graph `g`. Each new vertex is attached with `k` edges to `k` different vertices already present in the system by preferential attachment.

### Optional Arguments

  * `seed=-1`: set the RNG seed.

## Examples

```jldoctest
julia> g = cycle_graph(4)
{4, 4} undirected simple Int64 graph

julia> barabasi_albert!(g, 16, 3);

julia> g
{16, 40} undirected simple Int64 graph
```
