```
make_edge(n1::ComputeTaskNode, n2::DataTaskNode, index::Int)
```

Construct and return a new [`Edge`](@ref) pointing from `n1` (child) to `n2` (parent).

The index parameter is 0 by default and is passed to the parent node as argument index for its child.
