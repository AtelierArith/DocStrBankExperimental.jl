```
pipe_model!(node, root_value; name=:_cache_a7118a60b2a624134bf9eac2d64f2bb32798626a)
```

Computes the cross-section of `node` considering its topological environment and the cross-section at the root node (`root_value`).

The pipe model helps compute the cross-section of the nodes in an mtg by following the rule that the sum of the cross-sections of the children of a node is equal to the node cross-section.

The implementation uses the following algorithm:

First, check how many children a node has.

If it has one child only, the child cross-section is equal to the node cross-section.

If more children, the node cross-section is shared between the children according to the number of leaf nodes their subtree has, *i.e.* the total number of terminal nodes of their subtree.

Please call [`clean_cache!`](@ref) after using `pipe_model!` because it creates temporary variables.
