```
ladderize_tree(root::T, ascending::Bool=true)::T where T<:AbstractNode
```

This function returns a ladderized copy of a tree, i.e. a copy with all the nodes on all levels sorted by the count of their descendants.

  * `root` : root Node of tree.
  * `ascending` : Boolean, determines whether to sort in ascending (true) or                descending (false) order.
