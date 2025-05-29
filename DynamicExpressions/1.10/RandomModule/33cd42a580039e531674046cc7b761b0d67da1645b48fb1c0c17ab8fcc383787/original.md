```
NodeSampler(; tree, filter::Function=Returns(true), weighting::Union{Nothing,Function}=nothing, break_sharing::Val=Val(false))
```

Defines a sampler of nodes in a tree.

# Arguments

  * `tree`: The tree to sample nodes from. For a regular `Node`, nodes are sampled uniformly. For a `GraphNode`, nodes are also sampled uniformly (e.g., in `sin(x) + {x}`, the `x` has equal probability of being sampled from the `sin` or the `+` node, because it is shared), unless `break_sharing` is set to `Val(true)`.
  * `filter::Function`: A function that takes a node and returns a boolean indicating whether the node should be sampled. Defaults to `Returns(true)`.
  * `weighting::Union{Nothing,Function}`: A function that takes a node and returns a weight for the node, if it passes the filter, proportional to the probability of sampling the node. If `nothing`, all nodes are sampled uniformly.
  * `break_sharing::Val`: If `Val(true)`, the sampler will break sharing in the tree, and sample nodes uniformly from the tree.
