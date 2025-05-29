```
supports_missings_measure(atomic_measure)
```

Return a new measure, `measure`, with the same behavior as `atomic_measure`, but supporting `missing` as a value for `ŷ` or `y` in calls like `measure(ŷ, y, args...)`, or in applications of [`measurements`](@ref).  Missing values are propagated by the wrapped measure (but may be skipped in subsequent wrapping or aggregation).
