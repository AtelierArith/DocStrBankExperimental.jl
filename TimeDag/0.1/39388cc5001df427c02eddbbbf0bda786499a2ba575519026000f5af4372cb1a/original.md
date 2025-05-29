```
align_once(x, y) -> Node
```

Similar to `align(x, y)`, except knots from `x` will be emitted at most once.

This means that the resulting node will tick at a subset of the times that `y` ticks.
