```
estimate_boxsizes(X::AbstractStateSpaceSet; kwargs...) → εs
```

Return `k` exponentially spaced values: `εs = base .^ range(lower + w, upper + z; length = k)`, that are a good estimate for sizes ε that are used in calculating a fractal Dimension. It is strongly recommended to [`standardize`](@ref) input dataset before using this function.

Let `d₋` be the minimum pair-wise distance in `X`, `d₋ = dminimum_pairwise_distance(X)`. Let `d₊` be the average total length of `X`, `d₊ = mean(ma - mi)` with `mi, ma = minmaxima(X)`. Then `lower = log(base, d₋)` and `upper = log(base, d₊)`. Because by default `w=1, z=-1`, the returned sizes are an order of mangitude larger than the minimum distance, and an order of magnitude smaller than the maximum distance.

## Keywords

  * `w = 1, z = -1, k = 16` : as explained above.
  * `base = MathConstants.e` : the base used in the `log` function.
  * `warning = true`: Print some warnings for bad estimates.
  * `autoexpand = true`: If the final estimated range does not cover at least 2 orders of magnitude, it is automatically expanded by setting `w -= we` and `z -= ze`. You can set different default values to the keywords `we = w, ze = z`.
