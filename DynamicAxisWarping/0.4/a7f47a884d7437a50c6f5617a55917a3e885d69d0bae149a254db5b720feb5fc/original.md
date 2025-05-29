```
dtw_cost(a::AbstractArray, b::AbstractArray, dist::Distances.SemiMetric, r::Int; best_so_far = Inf, cumulative_bound = Zeros(length(a)))
```

Perform dynamic time warping to measure the distance between two sequences.

Calculate the DTW cost between `a` and `b` with maximum warping radius `r`. You may provide values of `best_so_far` and `cumulative_bound` in order to enable early stopping.

# Keyword arguments:

  * `best_so_far`: The best cost value obtained so far (optional)
  * `cumulative_bound`: A vector the same length as a and b (optional)
  * `s1`: Optional storage vector of length 2r+1, can be used to save allocations.
  * `s2`: Optional storage vector of length 2r+1, can be used to save allocations.

Providing the two vectors `s1, s2` does not save very much time, but it makes the function completely allocation free. Can be useful in a threaded context.

See also [`dtw`](@ref) and [`dtwnn`](@ref). This code was inspired by https://www.cs.ucr.edu/~eamonn/UCRsuite.html
