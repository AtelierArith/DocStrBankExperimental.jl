```
random_regular_graph(n::Int, k::Int, G=Graph; seed=-1)
```

Creates a random undirected [regular graph](https://en.wikipedia.org/wiki/Regular_graph) with `n` vertices, each with degree `k`.

For undirected graphs, allocates an array of `nk` `Int`s, and takes approximately $nk^2$ time. For $k > n/2$, generates a graph of degree `n-k-1` and returns its complement.

`G` is the resulting graph type.
