```
prepend(x, y) -> Node
```

Create a node that ticks with knots from `x` until `y` is active, and thereafter from `y`.

Note that the [`value_type`](@ref) of the returned node will be that of the promoted value types of `x` and `y`.
