```
disaggregate(object, scale; kw...)
```

Disaggregate array, or all arrays in a stack or series, by some scale.

# Arguments

  * `object`: Object to aggregate, like `AbstractRasterSeries`, `AbstractStack`, `AbstractRaster`, `Dimension` or `Lookup`.
  * `scale`: the aggregation factor, which can be an `Int`, a `Tuple` of `Int` for each dimension, or a `:` colon to mean the whole dimension.  You can also use any `Dimension`, `Selector` or `Int` combination you can usually use in `getindex`. `Tuple` of `Pair` or `NamedTuple` where keys are dimension names will also work. Using a `Selector` will determine the scale by the distance from the start  of the index. Selectors will find the first offset and repeat the same aggregation size for the rest.

# Keywords

  * `filename`: a filename to write to directly, useful for large files.
  * `suffix`: a string or value to append to the filename.   A tuple of `suffix` will be applied to stack layers. `keys(stack)` are the default.
  * `progress`: show a progress bar, `true` by default, `false` to hide.
  * `threaded`: run operations in parallel, `false` by default. In some circumstances `threaded`    can give large speedups over single-threaded operation. This can be true for complicated    geometries written into low-resolution rasters, but may not be for simple geometries with    high-resolution rasters. With very large rasters threading may be counter productive due    to excessive memory use. Caution should also be used: `threaded` should not be used in in-place    functions writing to `BitArray` or other arrays where race conditions can occur.
  * `lazy`: A `Bool` specifying if to disaggregate lazily. Defaults to `false`

Note: currently it is *much* faster to disaggregate over a memory-backed  source array. Use [`read`](@ref) on `src` before use where required.
