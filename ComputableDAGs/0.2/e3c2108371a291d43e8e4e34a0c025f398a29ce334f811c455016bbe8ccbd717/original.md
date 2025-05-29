```
ComputeTaskNode <: Node
```

Any node that computes a result from inputs using an [`AbstractComputeTask`](@ref).

# Fields

`.task`:            The node's compute task type. A concrete subtype of [`AbstractComputeTask`](@ref).
`.parents`:         A vector of the node's parents (i.e. nodes that depend on this one).
`.children`:        A vector of tuples with the node's children (i.e. nodes that this one depends on) and their index, used to order the arguments for the [`AbstractComputeTask`](@ref).
`.id`:              The node's id. Improves the speed of comparisons and is used as a unique identifier.
`.node_reduction`:  Either this node's [`NodeReduction`](@ref) or `missing`, if none. There can only be at most one.
`.node_split`:      Either this node's [`NodeSplit`](@ref) or `missing`, if none. There can only be at most one.
`.device`:          The Device this node has been scheduled on by a [`Scheduler`](@ref).
