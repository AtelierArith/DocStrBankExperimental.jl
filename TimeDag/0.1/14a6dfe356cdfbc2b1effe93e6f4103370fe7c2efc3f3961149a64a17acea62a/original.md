```
evaluate(nodes::AbstractVector{Node}, t0, t1[; batch_interval]) -> Vector{Block}
evaluate(node::Node, t0, t1[; batch_interval]) -> Block
```

Evaluate the specified node(s) over the specified time range `[t0, t1)`, and return the corresponding [`Block`](@ref)(s).

If `nodes` have common dependencies, work will not be repeated when performing this evaluation.
