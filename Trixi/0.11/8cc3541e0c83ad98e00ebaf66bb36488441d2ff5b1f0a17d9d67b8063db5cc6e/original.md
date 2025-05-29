```
max_abs_speed_naive(u_ll, u_rr, orientation::Integer, equations)
max_abs_speed_naive(u_ll, u_rr, normal_direction::AbstractVector, equations)
```

Simple and fast estimate of the maximal wave speed of the Riemann problem with left and right states `u_ll, u_rr`, based only on the local wave speeds associated to `u_ll` and `u_rr`.

For non-integer arguments `normal_direction` in one dimension, `max_abs_speed_naive` returns `abs(normal_direction[1]) * max_abs_speed_naive(u_ll, u_rr, 1, equations)`.
