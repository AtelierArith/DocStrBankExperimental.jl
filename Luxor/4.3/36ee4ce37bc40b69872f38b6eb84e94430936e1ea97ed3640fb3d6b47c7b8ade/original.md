```
between(p1::Point, p2::Point, x)
between((p1::Point, p2::Point), x)
```

Find the point between point `p1` and point `p2` for `x`, where `x` is typically between 0 and 1. `between(p1, p2, 0.5)` is equivalent to `midpoint(p1, p2)`.
