```
nodevalue(node)
```

Get the value associated with a node in a tree.  This removes wrappers such as [`Indexed`](@ref) or [`TreeCursor`](@ref)s.

By default, this function is the identity.

**OPTIONAL**: This should be implemented with any tree for which nodes have some "value" apart from the node itself. For example, integers cannot themselves be tree nodes, to create a tree in which the "nodes" are integers one can do something like

```julia
struct IntNode
    value::Int
    children::Vector{IntNode}
end

AbstractTrees.nodevalue(n::IntNode) = n.value
```
