```
aggregate!(method, dst::AbstractRaster, src::AbstractRaster, scale; skipmissing=false)
```

Aggregate raster `src` to raster `dst` by `scale`, using `method`.

# Arguments

  * `method`: a function such as `mean` or `sum` that can combine the value of multiple cells to generate the aggregated cell, or a [`Locus`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Dimensions.Lookups.locus) like `Start()` or `Center()` that species where to sample from in the interval.
  * `scale`: the aggregation factor, which can be an `Int`, a `Tuple` of `Int` for each dimension, or a `:` colon to mean the whole dimension.  You can also use any `Dimension`, `Selector` or `Int` combination you can usually use in `getindex`. `Tuple` of `Pair` or `NamedTuple` where keys are dimension names will also work. Using a `Selector` will determine the scale by the distance from the start  of the index. Selectors will find the first offset and repeat the same aggregation size for the rest.

When the aggregation `scale` of is larger than the array axis, the length of the axis is used.

# Keywords

  * `skipmissing`: if `true`, any `missingval` will be skipped during aggregation, so that   only areas of all missing values will be aggregated to `missingval(dst)`. If `false`,   aggregated areas containing one or more `missingval` will be assigned `missingval`.    `false` by default. `skipmissing` behaviour is independent of function `f`, which is   only applied to completely non-missing values.
  * `progress`: show a progress bar, `true` by default, `false` to hide.
  * `vebose`: whether to print messages about potential problems. `true` by default.

Note: currently it is *much* faster to aggregate over memory-backed source arrays. Use [`read`](@ref) on `src` before use where required.
