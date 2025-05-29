```
path_length(ancestor::T, descendant::T)::Float64  where T<:AbstractNode
```

Note: The function assumes there is an ancestral relationship between the two nodes.

This function calculates the length of the path separating the ancestor from the offspring node. The function follows the path specified through the binary description of the node.
