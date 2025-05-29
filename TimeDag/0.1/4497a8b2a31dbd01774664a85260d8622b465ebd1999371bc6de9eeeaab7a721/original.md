```
lag(x::Node, n::Integer)
```

Construct a node which takes values from `x`, but lags them by `n` knots.

This means that we do not introduce any new timestamps that do not appear in `x`, however we will not emit knots for the first `n` values that appear when evaluating `x`.

!!! note
    If `x` is a constant node, and `n > 0`, `lag(x, n)` will be an [`empty_node`](@ref) of the same [`value_type`](@ref) as `x`.

    Conceptually, this is consistent with the view that a constant is represented by a single knot at the start of time.

