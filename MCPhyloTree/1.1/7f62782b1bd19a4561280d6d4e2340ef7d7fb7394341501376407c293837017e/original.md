```
insert_node!(mother::T, children::Vector{T})::T where T<:AbstractNode
```

This function inserts a node into a tree after a mother node and gains a subset of the mother's children as its children.

Returns the inserted node.

  * `mother` : Node under which to add the newly-inserted node.
  * `children` : Children of node referenced by "mother" to reassign as children of the newly-inserted node.
