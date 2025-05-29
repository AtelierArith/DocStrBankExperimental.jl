```
coverage!(A, geom; [mode, scale])
```

Calculate the area of a raster covered by GeoInterface.jl compatible geometry `geom`, as a fraction.

Each pixel is assigned a grid of points (by default 10 x 10) that are each checked to be inside the geometry. The sum divided by the number of points to give coverage.

In practice, most pixel coverage is not calculated this way - shortcuts that  produce the same result are taken wherever possible.

If `geom` is an `AbstractVector` or table, the `mode` keyword will determine how coverage is combined.

# Keywords

  * `mode`: method for combining multiple geometries - `union` or `sum`. 

      * `union` (the default) gives the areas covered by all geometries. Usefull in spatial coverage where overlapping regions should not be counted twice. The returned raster will contain `Float64` values between `0.0` and `1.0`.
      * `sum` gives the summed total of the areas covered by all geometries, as in taking the sum of running `coverage` separately on all geometries. The returned values are positive `Float64`.

    For a single geometry, the `mode` keyword has no effect - the result is the same.
  * `scale`: `Integer` scale of pixel subdivision. The default of `10` means each pixel has    10 x 10 or 100 points that contribute to coverage. Using `100` means 10,000 points   contribute. Performance will decline as `scale` increases. Memory use will grow    by `scale^2` when `mode=:union`.
  * `threaded`: run operations in parallel, `false` by default. In some circumstances `threaded`    can give large speedups over single-threaded operation. This can be true for complicated    geometries written into low-resolution rasters, but may not be for simple geometries with    high-resolution rasters. With very large rasters threading may be counter productive due    to excessive memory use. Caution should also be used: `threaded` should not be used in in-place    functions writing to `BitArray` or other arrays where race conditions can occur.
  * `progress`: show a progress bar, `true` by default, `false` to hide.
  * `vebose`: whether to print messages about potential problems. `true` by default.
