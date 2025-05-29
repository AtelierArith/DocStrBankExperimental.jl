```
SampledField(v; x)
SampledField(v; z)
SampledField(v; x, y)
SampledField(v; x, z)
SampledField(v; x, y, z)
```

Create a sampled field from a data `v` that may depend on position. For 1D fields, the `x` or `z` coordinate is required, and `v` is a vector. For 2D fields, the `x` and `y` coordinates or the `x` and `z` coordinates are required, and `v` is a matrix. For 3D fields, the `x`, `y`, and `z` coordinates are required, and `v` is a 3D array.

Keyword argument `interp` is used to specify the interpolation method. `:linear` interpolation is supported for 1D, 2D and 3D fields. For 2D and 3D fields, the data must be sampled on a regular grid. For uniformly sampled `1D` fields, `:cubic` interpolation is also supported.
