```
X, y = make_circles(n=100; kwargs...)
```

Generate `n` labeled points close to two concentric circles for classification and clustering models.

### Return value

By default, a table `X` with `2` columns and `n` rows (observations), together with a corresponding vector of `n` `Multiclass` target observations `y`. The target is either `0` or `1`, corresponding to membership to the smaller or larger circle, respectively.

### Keyword arguments

  * `shuffle=true`: whether to shuffle the resulting points,
  * `noise=0`: standard deviation of the Gaussian noise added to the data,
  * `factor=0.8`: ratio of the smaller radius over the larger one,
  * `eltype=Float64`: machine type of points (any subtype of  `AbstractFloat`).
  * `rng=Random.GLOBAL_RNG`: any `AbstractRNG` object, or integer to seed a `MersenneTwister` (for reproducibility).
  * `as_table=true`: whether to return the points as a table (true) or a matrix (false). If `false` the target `y` has integer element type.

### Example

```julia
X, y = make_circles(100; noise=0.5, factor=0.3)
```
