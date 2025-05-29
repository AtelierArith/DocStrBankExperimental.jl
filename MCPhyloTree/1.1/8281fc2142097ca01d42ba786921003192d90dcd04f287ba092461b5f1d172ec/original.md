```
add_child!(mother_node::N, child::N)::Nothing where N <: GeneralNode
```

This function adds a child to the mother node. The arity of the mother node is increased by `1` and the root status of the child is set to `False`.

  * `mother_node` : Node to add a child to.
  * `child` : Node to add to mother_node.children.
