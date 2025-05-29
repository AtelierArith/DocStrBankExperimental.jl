```
RadonFlexibleCircle(N, in_height, out_height, weights)
```

  * `N` is the size of the first and second dimension of the input for `radon`.
  * `in_height` is a vector or range indicating the vertical positions of the rays entering the circle with respect to the midpoint which is located at `N ÷ 2 + 1`. Maximum and minimum values are `(N+1) ÷ 2 - 1` and `-(N+1) ÷ 2 + 1` respectively.
  * `out_height` is a vector or range indicating the vertical positions of the rays exiting the circle with respect to the midpoint which is located at `N ÷ 2 + 1`. Maximum and minimum values are `(N+1) ÷ 2 - 1` and `-(N+1) ÷ 2 + 1` respectively.

One definition could be: `RadonFlexibleCircle(10, -4:4, zeros((9,)))` It would describe rays which enter the circle at positions `-4:4` but all of them would focus at the position 0 when leaving the circle. This is an extreme form of fan beam tomography.

  * `weights` can weight each of the rays with different strength. Per default `weights = 0 .* in_height .+ 1`

See [`radon`](@ref) and [`backproject`](@ref) how to apply.
