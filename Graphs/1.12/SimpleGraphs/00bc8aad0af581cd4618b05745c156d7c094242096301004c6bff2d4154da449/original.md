```
barabasi_albert(n, k)
```

Create a [Barabási–Albert model](https://en.wikipedia.org/wiki/Barab%C3%A1si%E2%80%93Albert_model) random graph with `n` vertices. It is grown by adding new vertices to an initial graph with `k` vertices. Each new vertex is attached with `k` edges to `k` different vertices already present in the system by preferential attachment. Initial graphs are undirected and consist of isolated vertices by default.

### Optional Arguments

  * `is_directed=false`: if true, return a directed graph.
  * `complete=false`: if true, use a complete graph for the initial graph.
  * `rng=nothing`: set the Random Number Generator.
  * `seed=nothing`: set the RNG seed.

## Examples

```jldoctest
julia> using Graphs

julia> barabasi_albert(50, 3)
{50, 141} undirected simple Int64 graph

julia> barabasi_albert(100, Int8(10), is_directed=true, complete=true, seed=123)
{100, 990} directed simple Int8 graph
```
