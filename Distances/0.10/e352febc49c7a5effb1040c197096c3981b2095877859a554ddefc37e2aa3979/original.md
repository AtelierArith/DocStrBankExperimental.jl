```
pairwise(metric::PreMetric, a::AbstractMatrix, b::AbstractMatrix=a; dims)
```

Compute distances between each pair of rows (if `dims=1`) or columns (if `dims=2`) in `a` and `b` according to distance `metric`. If a single matrix `a` is provided, compute distances between its rows or columns.

`a` and `b` must have the same numbers of columns if `dims=1`, or of rows if `dims=2`.
