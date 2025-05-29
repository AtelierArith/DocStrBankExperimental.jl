```
AbstractNode{T}
```

Abstract type of tree nodes that implement the AbstractTrees.jl interface.

It is *NOT* necessary for tree nodes to inherit from this type to implement the AbstractTrees.jl interface. Conversely, all `AbstractNode` types are required to satisfy the AbstractTrees.jl interface (i.e. they must at least define [`children`](@ref)).

Package developers should keep in mind when writing methods that most trees *will not* be of this type. Therefore, any functions which are intended to work on any tree should not dispatch on `AbstractNode`.

The type parameter `T` is the type of the [`nodevalue`](@ref) of the concrete type descented from `AbstractNode`.
