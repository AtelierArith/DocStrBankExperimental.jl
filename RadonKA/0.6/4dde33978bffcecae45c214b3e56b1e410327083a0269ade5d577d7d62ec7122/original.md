```
RadonParallelCircle(N, in_height, weights)
```

  * `N` is the size of the first and second dimension of the input array for `radon`.
  * `in_height` is a vector or a range indicating the positions of the detector with respect to the midpoint which is located at `N ÷ 2 + 1`. The rays travel along straight parallel paths through the array. Maximum and minimum values are `(N+1) ÷ 2 - 1` and `-(N+1) ÷ 2 + 1` respectively.

For example, for an array of size `N=10` the default definition is: `RadonParallelCircle(10, -4:4)` So the resulting sinogram has the shape: `(9, length(angles), size(array, 3))`.

  * `weights` can weight each of the rays with different strength. Per default `weights = 0 .* in_height .+ 1`

See [`radon`](@ref) and [`backproject`](@ref) how to apply.
