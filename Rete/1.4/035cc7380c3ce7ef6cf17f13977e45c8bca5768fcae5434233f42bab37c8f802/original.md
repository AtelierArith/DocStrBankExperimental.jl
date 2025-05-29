```
askc(continuation, root::AbstractReteRootNode, t::Type)
```

calls `continuation` on every fact of the specified type that are stored in the network rooted at `root`.

Does not consider subtypes because that could lead to `continuation` being called on the same fact more than once (from the memory node for the type itself and from the memory nodes of subtypes).

Assumes all memory nodes are direct outputs of `root`.

Also assumes that every output of `root` implements `is_memory_for_type`.
