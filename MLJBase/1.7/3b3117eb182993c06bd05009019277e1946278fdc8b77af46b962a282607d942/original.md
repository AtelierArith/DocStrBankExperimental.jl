```
make_regression(n, p; kwargs...)
```

Generate Gaussian input features and a linear response with Gaussian noise, for use with regression models.

### Return value

By default, a tuple `(X, y)` where table `X` has `p` columns and `n` rows (observations), together with a corresponding vector of `n` `Continuous` target observations `y`.

### Keywords

  * `intercept=true`: Whether to generate data from a model with intercept.
  * `n_targets=1`: Number of columns in the target.
  * `sparse=0`: Proportion of the generating weight vector that is sparse.
  * `noise=0.1`: Standard deviation of the Gaussian noise added to the response (target).
  * `outliers=0`: Proportion of the response vector to make as outliers by adding a random quantity with high variance. (Only applied if `binary` is `false`.)
  * `as_table=true`: Whether `X` (and `y`, if `n_targets > 1`) should be a table or a matrix.
  * `eltype=Float64`: Element type for `X` and `y`. Must subtype `AbstractFloat`.
  * `binary=false`: Whether the target should be binarized (via a sigmoid).
  * `eltype=Float64`: machine type of points (any subtype of  `AbstractFloat`).
  * `rng=Random.GLOBAL_RNG`: any `AbstractRNG` object, or integer to seed a `MersenneTwister` (for reproducibility).
  * `as_table=true`: whether to return the points as a table (true) or a matrix (false).

### Example

```julia
X, y = make_regression(100, 5; noise=0.5, sparse=0.2, outliers=0.1)
```
