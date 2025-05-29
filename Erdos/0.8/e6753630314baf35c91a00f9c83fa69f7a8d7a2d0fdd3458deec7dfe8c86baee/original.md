```
barabasi_albert!(g, n::Int, k::Int; seed::Int = -1)
```

Grows the graph `g` according to [Barabási–Albert](https://en.wikipedia.org/wiki/Barab%C3%A1si%E2%80%93Albert_model) process into a graph with `n` vertices. At each step a new vertex is attached by preferential attachment to `k` different vertices already present in the graph.

See also [`barabasi_albert`](@ref).
