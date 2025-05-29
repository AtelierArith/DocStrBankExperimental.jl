```
pairwise!(metric::PreMetric, r::AbstractMatrix, a, b=a)
```

Compute distances between each element of collection `a` and each element of collection `b` according to distance `metric`, and store the result in `r`. If a single iterable `a` is provided, compute distances between its elements.

`r` must be a matrix with size `length(a) × length(b)`.
