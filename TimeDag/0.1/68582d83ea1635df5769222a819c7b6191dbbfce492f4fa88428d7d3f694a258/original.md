```
constant(value) -> Node
constant(T, value) -> Node{T}
```

Explicitly wrap `value` into a `TimeDag` constant node, regardless of its type.

If `T` is provided, this allows creation of a node with a [`value_type`](@ref) that is a supertype of the type of the `value` — otherwise the constant node will always just use the concrete type of `value`.

In many cases this isn't required, since many `TimeDag` functions which expect nodes will automatically wrap non-node arguments into a constant node.

!!! warning
    If `value` is already a node, this will wrap it up in an additional node. This is very likely not what you want to do.

