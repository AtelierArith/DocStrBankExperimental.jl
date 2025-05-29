```
remove_child!(mother_node::N, left::Bool)::N where N <: GeneralNode
```

This function removes a child from the list of nodes which are daughters of this node. An input of "True" removes the left child, while "False" removes the right child.

Returns the removed node.

  * `mother_node` : Node from which to remove a child.
  * `left` : boolean value determining which child of mother_node to remove.
