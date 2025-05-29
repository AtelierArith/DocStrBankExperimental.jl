```
make_moons(n::Int=100; kwargs...)
```

Generates labeled two-dimensional points lying close to two interleaved semi-circles, for use with classification and clustering models.

### Return value

By default, a table `X` with `2` columns and `n` rows (observations), together with a corresponding vector of `n` `Multiclass` target observations `y`. The target is either `0` or `1`, corresponding to membership to the left or right semi-circle.

### Keyword arguments

  * `shuffle=true`: whether to shuffle the resulting points,
  * `noise=0.1`: standard deviation of the Gaussian noise added to the data,
  * `xshift=1.0`: horizontal translation of the second center with respect to the first one.
  * `yshift=0.3`: vertical translation of the second center with respect to the first one.
  * `eltype=Float64`: machine type of points (any subtype of  `AbstractFloat`).
  * `rng=Random.GLOBAL_RNG`: any `AbstractRNG` object, or integer to seed a `MersenneTwister` (for reproducibility).
  * `as_table=true`: whether to return the points as a table (true) or a matrix (false). If `false` the target `y` has integer element type.

### Example

```julia
X, y = make_moons(100; noise=0.5)
```
