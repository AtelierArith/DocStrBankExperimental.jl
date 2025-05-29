```
make_random_psd_matrix_from_wishart(
    num_assets::Integer,
    rng::Union{MersenneTwister,StableRNG} = MersenneTwister(1),
)
```

Make a random psd matrix from the inverse wishart distribution.

### Inputs

  * `num_assets` - The number of assets.
  * `rng` - The Random.MersenneTwister or StableRNGs.Stable used for RNG.

### Returns

  * A `Hermitian`
