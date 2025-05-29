```
StableNode{T} <: AbstractNode{T}
```

A node belonging to a tree in which all nodes are of type `StableNode{T}`.  This type is provided so that trees with [`NodeTypeUnknown`](@ref) can implement methods to be converted to type-stable trees with indexable `children` which allow for efficient traversal and iteration.

## Constructors

```julia
StableNode{T}(x::T, ch)
StableNode(x, ch=())
StableNode{T}(𝒻, node)
```

## Arguments

  * `x`: the value of the constructed node, returned by [`nodevalue`](@ref).
  * `ch`: the children of the node, each must be of type `StableNode`.
  * `𝒻`: A function which, when called on the node of a tree returns a value which should be wrapped   by a `StableNode`.  The return value of `𝒻` must be convertible to `T` (see example).
  * `T`: The value type of the `StableNode`s in a tree.
  * `node`: A node from a tree which is to be used to construct the `StableNode` tree.

## Examples

```julia
t = [1, [2,3]]

node = StableNode{Union{Int,Nothing}}(t) do n
    n isa Integer ? convert(Int, n) : nothing
end
```

In the above example `node` is a tree with [`HasNodeType`](@ref), nodes of type `StableNode{Union{Int,Nothing}}`. The nodes in the new tree corresponding to arrays have value `nothing` while other nodes have their corresponding `Int` value.
