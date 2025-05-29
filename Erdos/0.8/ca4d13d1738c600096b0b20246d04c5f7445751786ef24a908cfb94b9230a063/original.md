```
struct ConstEdgeMap{T} <: SimpleEdgeMap{T}
    val::T
end
```

A type representing a constant vector map. Any attempt to change the internal value, e.g. `emap[u,v] = 4`, will fail silently.
