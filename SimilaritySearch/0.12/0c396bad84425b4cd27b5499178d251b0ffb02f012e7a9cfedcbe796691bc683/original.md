```
append_items!(
    index::SearchGraph,
    context::SearchGraphContext,
    db
)
```

Appends all items in db to the index. It can be made in parallel or sequentially.

# Arguments:

  * `index`: the search graph index
  * `db`: the collection of objects to insert, an `AbstractDatabase` is the canonical input, but supports any iterable objects
  * `context`: The context environment of the graph, see  [`SearchGraphContext`](@ref).
