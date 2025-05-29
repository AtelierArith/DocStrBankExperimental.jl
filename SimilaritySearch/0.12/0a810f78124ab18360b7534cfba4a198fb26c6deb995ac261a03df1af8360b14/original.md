```
push_item!(
    index::SearchGraph,
    context,
    item,
    push_item
)
```

Appends an object into the index. Internal function

Arguments:

  * `index`: The search graph index where the insertion is going to happen.
  * `item`: The object to be inserted, it should be in the same space than other objects in the index and understood by the distance metric.
  * `context`: The context environment of the graph, see  [`SearchGraphContext`](@ref).
  * `push_db`: if `false` is an internal option, used by `append!` and `index!` (it avoids to insert `item` into the database since it is already inserted but not indexed).
  * Note: setting `callbacks` as `nothing` ignores the execution of any callback
