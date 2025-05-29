```
colwise!(metric::PreMetric, r::AbstractArray,
         a::AbstractMatrix, b::AbstractMatrix)
colwise!(metric::PreMetric, r::AbstractArray,
         a::AbstractVector, b::AbstractMatrix)
colwise!(metric::PreMetric, r::AbstractArray,
         a::AbstractMatrix, b::AbstractVector)
```

Compute distances between each corresponding columns of `a` and `b` according to distance `metric`, and store the result in `r`. Exactly one of `a` or `b` can be a vector, in which case the distance between that vector and all columns of the other matrix are computed.

`a` and `b` must have the same number of columns if neither of the two is a vector. `r` must be an array of length `maximum(size(a, 2), size(b, 2))`.

!!! note
    If both `a` and `b` are vectors, the generic, iterator-based method of `colwise` applies.

