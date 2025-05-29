```
push_item!(
    index::SearchGraph,
    context,
    item;
    push_item=true
)
```

Appends an object into the index.

Arguments:

  * `index`: The search graph index where the insertion is going to happen
  * `item`: The object to be inserted, it should be in the same space than other objects in the index and understood by the distance metric.
  * `context`: The context environment of the graph, see  [`SearchGraphContext`](@ref).
  * `push_db`: if `push_db=false` is an internal option, used by `append!` and `index!` (it avoids to insert `item` into the database since it is already inserted but not indexed)
