```
SimpleDiGraph{T}(g::AbstractGraph)
SimpleDiGraph(g::AbstractGraph)
```

Construct a `SimpleDiGraph` from any `AbstractGraph` by enumerating edges.

If `g` is undirected, both directed edges `(u, v)` and `(v, u)` are added if undirected edge `{u, v}` exists.
