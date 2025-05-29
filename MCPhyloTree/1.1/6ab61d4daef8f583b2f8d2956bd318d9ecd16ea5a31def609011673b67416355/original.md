```
find_num(root::T, num::Int64)  where T<:AbstractNode
```

Find a node by its number. The function assumes that the node is present in the tree.

Do not use this function if you are unsure whether the node is in the tree at all.

Returns reference to Node.

  * `root` : root Node of tree to be searched.
  * `num` : number of desired Node.
