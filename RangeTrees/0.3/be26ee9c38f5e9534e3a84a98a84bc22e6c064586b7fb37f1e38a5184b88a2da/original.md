```
intersect!(result::Vector{UnitRange{T}}, target::AbstractUnitRange, rn::RangeNode{T}) where {T}
```

Recursively intersect `target` with the intervals in the tree rooted at `rn`.

Non-empty intersections are pushed onto `result` in the same order as the intersecting nodes appear in the tree. Storing `maxlast` allows for the pre-order depth-first search to be truncated when a node's `maxlast` is less than `first(target)`.  Because the nodes are in non-decreasing order of `first(intvl)` the right subtree can be skipped when `last(target) < first(intvl)`.
