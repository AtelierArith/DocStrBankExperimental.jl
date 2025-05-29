```
IndexNode{T,I}
```

The node of a tree which implements the indexed tree interface.  Such a tree consists of an object `tree` from which nodes can be obtained with the two-argument method of [`nodevalue`](@ref) which by default calls `getindex`.

An `IndexNode` implements the tree interface, and can be thought of an adapter from an object that implements the indexed tree interface to one that implements the tree interface.

`IndexNode` do not store the value associated with the node but can obtain it by calling [`nodevalue`](@ref).

## Constructors

```julia
IndexNode(tree, node_index)

IndexNode(tree) = IndexNode(tree, rootindex(tree))  # one-argument constructor requires `rootindex`
```

Here `tree` is an object which stores or can obtain information for the entire tree structure, and `node_index` is the index of the node for which `node_index` is being constructed.
