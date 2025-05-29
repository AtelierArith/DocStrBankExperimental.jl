```
pairwise!(metric::PreMetric, r::AbstractMatrix,
          a::AbstractMatrix, b::AbstractMatrix=a; dims)
```

Compute distances between each pair of rows (if `dims=1`) or columns (if `dims=2`) in `a` and `b` according to distance `metric`, and store the result in `r`. If a single matrix `a` is provided, compute distances between its rows or columns.

`a` and `b` must have the same numbers of columns if `dims=1`, or of rows if `dims=2`. `r` must be a matrix with size `size(a, dims) × size(b, dims)`.
