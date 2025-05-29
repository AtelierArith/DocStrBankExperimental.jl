```
bd_coef_between(causet, i, j, dim, locality[, max_cardinality]) -> Float64
```

Return the Benincasa-Dowker coefficient at spacetime atom `i` with respect to spacetime atom `j`, or `0` if the two atoms aren't related or `max_cardinality` is exceeded.
