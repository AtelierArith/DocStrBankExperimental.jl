```
find_binary(root::T, bin::String)::T where T<:AbstractNode
```

Find a node by its binary representation. The function assumes that the node is present in the tree.

Do not use this function if you are unsure whether the node is in the tree at all.

Returns a reference to the desired Node.

  * `root` : root Node of tree to search.
  * `bin` : binary representation of desired Node as a String.
