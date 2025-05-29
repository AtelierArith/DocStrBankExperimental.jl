```
random_regular_digraph(n, k)
```

Create a random directed [regular graph](https://en.wikipedia.org/wiki/Regular_graph) with `n` vertices, each with degree `k`.

### Optional Arguments

  * `dir=:out`: the direction of the edges for degree parameter.
  * `seed=-1`: set the RNG seed.

### Implementation Notes

Allocates an $n × n$ sparse matrix of boolean as an adjacency matrix and uses that to generate the directed graph.
