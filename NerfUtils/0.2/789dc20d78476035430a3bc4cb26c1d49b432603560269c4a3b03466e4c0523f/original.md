```
function GridEncoding(
    kab; n_dims::Int = 3, n_levels::Int = 16, scale::Float32 = 1.5f0,
    base_resolution::Int = 16, n_features::Int = 2, hashmap_size::Int = 19,
    align_corners::Bool = true, store_level_ids::Bool = false)
```

Multiresolution Hash Encoding

# Arguments:

  * `kab`: Backend on which to instantiate `GridEncoding`.
  * `n_dims::Int`: Number of input dimensions (e.g. for 3D points it must be 3).
  * `n_levels::Int`: Number of levels in the grid. Higher number of levels   results in better accuracy at the expense of device memory.
  * `scale::Float32`: By how much to scale each next level in size.
  * `base_resolution::Int`: Initial resolution (1st level).
  * `n_features::Int`: Size of the features at each level.
  * `hashmap_size::Int`: log₂ size of the level at which it will switch from   one-to-one mapping to hashing.
  * `align_corners::Bool`: If `true` then grid corners when scaling inputs   to a respective level resolution.
  * `store_level_ids::Bool`: If `true` `GridEncoding` will store mapping id   from each feature to its level in the grid. This allows implementing   `GridEncoding` parameter decay as `mean(scatter(mean, θ.^2, level_ids))`.   Indices are stored in `Int8` type to reduce memory usage.

# Reference:

[https://nvlabs.github.io/instant-ngp/](https://nvlabs.github.io/instant-ngp/)
