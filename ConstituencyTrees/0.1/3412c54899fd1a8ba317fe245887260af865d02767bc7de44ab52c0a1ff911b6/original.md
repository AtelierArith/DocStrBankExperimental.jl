```
collapse_unary(tree, labelf=unary_label; collapse_pos=false, collapse_root=false)
```

Transform a parse tree by collapsing all single-child nodes.

# Arguments

  * `tree`: parse tree to transform
  * `labelf`: function called to create new label representing the collapsed nodes.

# Keywords

  * `collapse_pos=false`: whether to collapse `(POS word)` nodes
  * `collapse_root=false`: whether to collapse the top-level root node

# Returns

  * a transformed tree of the same type as its argument
