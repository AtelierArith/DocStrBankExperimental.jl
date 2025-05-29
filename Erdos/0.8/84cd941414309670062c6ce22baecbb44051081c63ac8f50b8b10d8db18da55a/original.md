```
barabasi_albert(n, k, G=Graph; seed=-1)
barabasi_albert(n, n0, k, G=Graph; seed=-1)
```

Creates a random graph of type `G` with `n` vertices according to [Barabási–Albert model](https://en.wikipedia.org/wiki/Barab%C3%A1si%E2%80%93Albert_model). It is grown by adding new vertices to an initial graph with `n0` vertices (`n0=k` if not specified). Each new vertex is attached with `k` edges to `k` different vertices already present in the system by preferential attachment. The initial graph is empty by default.

Undirected graphs are created by default. Directed graphs can be created passing a directed graph type as last argument (e.g. `DiGraph`).

See also [`barabasi_albert!`](@ref) for growing a given graph.
