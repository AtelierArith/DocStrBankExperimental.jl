```
get_upper_bounds(optimizer::BendersAlgorithm; monotonic = true)
```

Return the value of `upper_bounds` from the `BendersAlgorithm` object. This is a vector of the upper bounds at each iteration. The upper bound returned by each iteration is not guaranteed to decrease monotonically. If `monotonic=true`, this function returns the best upper bound seen up to each iteration (rather than the value of the feasible solution seen at that iteration)
