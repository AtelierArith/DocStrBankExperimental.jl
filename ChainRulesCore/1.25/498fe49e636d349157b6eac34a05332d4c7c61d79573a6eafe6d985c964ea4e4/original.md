```
add!!(x, y)
```

Returns `x+y`, potentially mutating `x` in-place to hold this value. This avoids allocations when `x` can be mutated in this way.
