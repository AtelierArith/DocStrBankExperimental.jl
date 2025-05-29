```
colwise!(metric::PreMetric, r::AbstractArray, a, b)
```

Compute distances between corresponding elements of the iterable collections `a` and `b` according to distance `metric`, and store the result in `r`.

`a` and `b` must have the same number of elements, `r` must be an array of length `length(a) == length(b)`.
