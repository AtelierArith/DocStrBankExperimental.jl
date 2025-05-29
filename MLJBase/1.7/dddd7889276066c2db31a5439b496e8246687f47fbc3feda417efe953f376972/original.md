```
X, y = make_blobs(n=100, p=2; kwargs...)
```

Generate Gaussian blobs for clustering and classification problems.

### Return value

By default, a table `X` with `p` columns (features) and `n` rows (observations), together with a corresponding vector of `n` `Multiclass` target observations `y`, indicating blob membership.

### Keyword arguments

  * `shuffle=true`: whether to shuffle the resulting points,
  * `centers=3`: either a number of centers or a `c x p` matrix with `c` pre-determined centers,
  * `cluster_std=1.0`: the standard deviation(s) of each blob,
  * `center_box=(-10. => 10.)`: the limits of the `p`-dimensional cube within which the cluster centers are drawn if they are not provided,
  * `eltype=Float64`: machine type of points (any subtype of  `AbstractFloat`).
  * `rng=Random.GLOBAL_RNG`: any `AbstractRNG` object, or integer to seed a `MersenneTwister` (for reproducibility).
  * `as_table=true`: whether to return the points as a table (true) or a matrix (false). If `false` the target `y` has integer element type.

### Example

```julia
X, y = make_blobs(100, 3; centers=2, cluster_std=[1.0, 3.0])
```
