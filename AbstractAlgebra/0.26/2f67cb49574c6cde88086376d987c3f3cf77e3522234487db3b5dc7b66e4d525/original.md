```
divexact(x, y; check::Bool=true)
```

Return an exact quotient of `x` by `y`, i.e. an element `z` such that `x == yz`; when `x` and `y` do not belong to the same ring, they are first coerced into a common ring. By default if no exact division is possible, an exception is raised. If `check=false` this check may be omitted for performance reasons and the behaviour of the function undefined if the division is not exact.
