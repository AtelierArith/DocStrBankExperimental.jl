```
edges(g::IndexedGraph, i::Integer)
```

Return a lazy iterators to the edges incident to `i`.

By default unordered edges sort source and destination nodes in increasing order. See [`outedges`](@ref outedges(g::IndexedGraph, i::Integer)) and [`inedges`](@ref inedges(g::IndexedGraph, i::Integer)) if you need otherwise.
