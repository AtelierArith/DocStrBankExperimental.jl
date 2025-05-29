```
CladoNode <: AbstractNode

CladoNode(node::ChronoNode) :: CladoNode
```

Type for nodes in a [`CladoTree`](@ref). 

A [`ChronoNode`](@ref) can be converted to a `CladoNode` by removing all  information about time.
