```
colwise(metric::PreMetric, a::AbstractMatrix, b::AbstractMatrix)
colwise(metric::PreMetric, a::AbstractVector, b::AbstractMatrix)
colwise(metric::PreMetric, a::AbstractMatrix, b::AbstractVector)
```

Compute distances between corresponding columns of `a` and `b` according to distance `metric`. Exactly one of `a` or `b` can be a vector, in which case the distance between that vector and all columns of the other matrix are computed.

`a` and `b` must have the same number of columns if neither of the two is a vector.

!!! note
    If both `a` and `b` are vectors, the generic, iterator-based method of `colwise` applies.

