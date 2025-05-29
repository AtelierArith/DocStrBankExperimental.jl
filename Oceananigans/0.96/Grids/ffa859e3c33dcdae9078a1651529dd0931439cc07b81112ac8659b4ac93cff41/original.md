```
nodes(grid, (ℓx, ℓy, ℓz); reshape=false, with_halos=false)
nodes(grid, ℓx, ℓy, ℓz; reshape=false, with_halos=false)
```

Return a 3-tuple of views over the interior nodes of the `grid`'s native coordinates at the locations in `loc=(ℓx, ℓy, ℓz)` in `x, y, z`.

If `reshape=true`, the views are reshaped to 3D arrays with non-singleton dimensions 1, 2, 3 for `x, y, z`, respectively. These reshaped arrays can then be used in broadcast operations with 3D fields or arrays.

For `RectilinearGrid`s the native coordinates are `x, y, z`; for curvilinear grids, like `LatitudeLongitudeGrid` or `OrthogonalSphericalShellGrid` the native coordinates are `λ, φ, z`.

See [`xnodes`](@ref), [`ynodes`](@ref), [`znodes`](@ref), [`λnodes`](@ref), and [`φnodes`](@ref).
