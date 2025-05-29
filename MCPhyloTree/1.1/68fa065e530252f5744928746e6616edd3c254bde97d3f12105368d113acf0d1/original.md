```
remove_child!(mother_node::N, child::N)::N where N<:AbstractNode
```

This function removes a child from the list of nodes which are daughters of this node.

The removed node is returned.

  * `mother_node` : Node from which to remove a child.
  * `child` : specific Node to remove. This node has to be a child of `mother_node`.
