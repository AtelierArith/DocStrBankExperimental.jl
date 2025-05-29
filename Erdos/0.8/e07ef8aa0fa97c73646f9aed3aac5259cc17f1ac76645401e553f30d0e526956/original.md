```
struct IndexedEdge <: AIndexedEdge
    src::Int
    dst::Int
    idx::Int
end
```

An indexed edge type

```
IndexedEdge(u, v) = IndexedEdge(u,v,-1)
```

Creates an edge with invalid index.
