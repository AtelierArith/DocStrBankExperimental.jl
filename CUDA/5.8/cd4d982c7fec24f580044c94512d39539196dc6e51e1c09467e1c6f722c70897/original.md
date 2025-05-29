```
CuTexture{T,N,P}(parent::P; address_mode, filter_mode, normalized_coordinates)
```

Construct a `N`-dimensional texture object with elements of type `T` as stored in `parent`.

Several keyword arguments alter the behavior of texture objects:

  * `address_mode` (wrap, *clamp*, mirror): how out-of-bounds values are accessed. Can be specified as a value for all dimensions, or as a tuple of `N` entries.
  * `interpolation` (*nearest neighbour*, linear, bilinear): how non-integral indices are fetched. Nearest-neighbour fetches a single value, others interpolate between multiple.
  * `normalized_coordinates` (true, *false*): whether indices are expected to fall in the normalized `[0:1)` range.

!!! warning Experimental API. Subject to change without deprecation.
