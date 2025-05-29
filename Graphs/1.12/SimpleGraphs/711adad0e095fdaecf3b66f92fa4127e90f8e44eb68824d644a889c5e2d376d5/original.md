```
SimpleGraph{T}(g::AbstractGraph)
SimpleGraph(g::AbstractGraph)
```

Construct a `SimpleGraph` from any `AbstractGraph` by enumerating edges.

If `g` is directed, a directed edge `{u, v}` is added if either directed edge `(u, v)` or `(v, u)` exists.
