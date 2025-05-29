```
between(p1::Point, p2::Point, r:range)
between(p1::Point, p2::Point, a:array)
```

Return an array of Points between point `p1` and point `p2` for every `x` in range `r` or array `a`.

If `x` is 0.0, that point will be at `p1`; if `x` is 1.0, that point will be at `p2`.

When `x` is 0.5, that point is the midpoint between `p1` and `p2`.
