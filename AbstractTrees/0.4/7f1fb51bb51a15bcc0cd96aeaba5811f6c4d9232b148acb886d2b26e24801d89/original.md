```
MapNode{T,C}
```

A node in a tree which is returned by [`treemap`](@ref).  It consists of a value which is the result of the function call and an array of the children, which are also of type `MapNode`.

Every `MapNode` is itself a tree with the [`IndexedChildren`](@ref) trait and therefore supports indexing via [`getdescendant`](@ref).

Use [`AbstractTrees.nodevalue`](@ref) or `mapnode.value` to obtain the wrapped value.
