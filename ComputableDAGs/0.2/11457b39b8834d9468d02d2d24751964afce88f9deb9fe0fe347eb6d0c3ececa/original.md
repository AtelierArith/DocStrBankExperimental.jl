```
partners(node::Node)
```

Return a vector of all partners of this node. 

A node's partners are all parents of any of its children. The result contains no duplicates and includes the node itself.

!!! note
    This is very slow when there are multiple children with many parents.  This is less of a problem in [`siblings(node::Node)`](@ref) because (depending on the model) there are no nodes with a large number of children, or only a single one.

