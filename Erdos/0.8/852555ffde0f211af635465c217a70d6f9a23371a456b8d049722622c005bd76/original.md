```
random_regular_digraph(n::Int, k::Int; dir::Symbol=:out, seed=-1)
```

Creates a random directed [regular graph](https://en.wikipedia.org/wiki/Regular_graph) with `n` vertices, each with degree `k`. The degree (in or out) can be specified using `dir=:in` or `dir=:out`.

For directed graphs, allocates an $n 	imes n$ sparse matrix of boolean as an adjacency matrix and uses that to generate the  graph.
