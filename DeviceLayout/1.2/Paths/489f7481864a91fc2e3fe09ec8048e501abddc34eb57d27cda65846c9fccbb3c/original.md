```
bspline!(p::Path{T}, nextpoints, α_end, sty::Style=contstyle1(p), endpoints_speed=2500μm)
```

Add a BSpline interpolation from the current endpoint of `p` through `nextpoints`.

The interpolation reaches `nextpoints[end]` making the angle `α_end` with the positive x-axis. The `endpoints_speed` is "how fast" the interpolation leaves and enters its endpoints. Higher speed means that the start and end angles are approximately α1(p) and α_end over a longer distance.
