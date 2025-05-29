```
NodePattern <: AbstractNodeLike
```

A `NodePattern` is a `Node`-like object that can be used to match nodes  in a graph.

We use `IDType` to allow for matching by ID, or by other properties.  If `IDType` is not nothing, then the pattern will match by ID. If  `IDType` is nothing, the pattern will match by labels and properties,  otherwise, it will start by matching by ID.

The only difference between a `NodePattern` and a `Node` is that a  `NodePattern` may not have an ID.
