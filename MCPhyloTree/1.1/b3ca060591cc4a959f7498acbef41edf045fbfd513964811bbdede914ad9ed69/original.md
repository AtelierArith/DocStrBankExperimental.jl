```
ladderize_tree!(root::T, ascending::Bool=true) where T<:AbstractNode
```

This function ladderizes a tree inplace, i.e. sorts the nodes on all levels by the count of their descendants.

  * `root` : root Node of tree.
  * `ascending` : Boolean, determines whether to sort in ascending (true) or               descending (false) order.
