```
throttle(x::Node, n::Integer) -> Node
```

Return a node that only ticks every `n` knots.

The first knot encountered on the input will always be emitted.

!!! info
    The throttled node is stateful and depends on the starting point of the evaluation.

