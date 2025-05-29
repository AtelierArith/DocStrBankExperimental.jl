```
index!(index::SearchGraph, context::SearchGraphContext)
```

Indexes the already initialized database (e.g., given in the constructor method). It can be made in parallel or sequentially. The arguments are the same than `append_items!` function but using the internal `index.db` as input.

# Arguments:

  * `index`: The graph index
  * `context`: The context environment of the graph, see  [`SearchGraphContext`](@ref).
