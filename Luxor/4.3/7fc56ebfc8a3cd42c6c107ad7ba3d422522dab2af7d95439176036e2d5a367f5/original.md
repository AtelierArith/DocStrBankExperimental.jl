```
isarcclockwise(c::Point, A::Point, B::Point)
```

Return `true` if an arc centered at `c` going from `A` to `B` is clockwise.

If `c`, `A`, and `B` are collinear, then a hemispherical arc could be either clockwise or not.
