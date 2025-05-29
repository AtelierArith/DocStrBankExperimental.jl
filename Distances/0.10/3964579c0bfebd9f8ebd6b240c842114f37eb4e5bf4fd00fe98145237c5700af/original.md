```
colwise(metric::PreMetric, a, b)
```

Compute distances between corresponding elements of the iterable collections `a` and `b` according to distance `metric`.

`a` and `b` must have the same number of elements (`length(a) == length(b)`).
