```
DataTaskNode <: Node
```

Any node that transfers data and does no computation.

# Fields

`.task`:            The node's data task type. Usually [`DataTask`](@ref).
`.parents`:         A vector of the node's parents (i.e. nodes that depend on this one).
`.children`:        A vector of tuples of the node's children (i.e. nodes that this one depends on) and their indices, indicating their order in the resulting function call passed to the task.
`.id`:              The node's id. Improves the speed of comparisons and is used as a unique identifier.
`.node_reduction`:  Either this node's [`NodeReduction`](@ref) or `missing`, if none. There can only be at most one.
`.node_split`:      Either this node's [`NodeSplit`](@ref) or `missing`, if none. There can only be at most one.
`.name`:            The name of this node for entry nodes into the graph ([`is_entry_node`](@ref)) to reliably assign the inputs to the correct nodes when executing.

