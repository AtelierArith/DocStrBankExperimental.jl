```
pathlength_nearest(seg::Paths.Segment, pt::Point)
```

Return `s` on `seg` that minimizes `norm(seg(s) - pt)`.

`s` will be between `zero(s)` and `pathlength(seg)`.
