```
barabasi_albert(n::Integer, n0::Integer, k::Integer)
```

Create a [Barabási–Albert model](https://en.wikipedia.org/wiki/Barab%C3%A1si%E2%80%93Albert_model) random graph with `n` vertices. It is grown by adding new vertices to an initial graph with `n0` vertices. Each new vertex is attached with `k` edges to `k` different vertices already present in the system by preferential attachment. Initial graphs are undirected and consist of isolated vertices by default.

### Optional Arguments

  * `is_directed=false`: if true, return a directed graph.
  * `complete=false`: if true, use a complete graph for the initial graph.
  * `seed=-1`: set the RNG seed.

## Examples

```jldoctest
julia> barabasi_albert(10, 3, 2)
{10, 14} undirected simple Int64 graph

julia> barabasi_albert(100, Int8(10), 3, is_directed=true, seed=123)
{100, 270} directed simple Int8 graph
```
