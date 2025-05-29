```
degree_histogram(g, degfn=degree)
```

Return a `Dict` with values representing the number of vertices that have degree represented by the key.

Degree function (for example, [`indegree`](@ref) or [`outdegree`](@ref)) may be specified by overriding `degfn`.
