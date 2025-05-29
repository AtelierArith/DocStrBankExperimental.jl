```
watts_strogatz(n, k, β, G=Graph; seed=-1)
```

Creates a [Watts-Strogatz](https://en.wikipedia.org/wiki/Watts_and_Strogatz_model) small model random graph with `n` vertices, each with degree `k`. Edges are randomized per the model based on probability `β`.

Undirected graphs are created by default. Directed graphs can be created passing a directed graph type as last argument (e.g. `DiGraph`).
