```
robust_measure(measure)
```

Return a new measure `robust` such that:

  * `weights` and `class_weights` are silently treated as uniform (unit) if unsupported by `measure`
  * if either `weights` or `class_weights` is `nothing`, it is as if the argument is omitted (interpreted as uniform)

This holds for all calls of the form `robust(ŷ, y, weights, class_weights)` or `measurements(robust, ŷ, y, weights, class_weights)` and otherwise the behavior of `robust` is the same as for `measure`.
